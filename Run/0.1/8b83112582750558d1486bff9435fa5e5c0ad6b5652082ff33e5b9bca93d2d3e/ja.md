# Run

[![Stable](https://img.shields.io/badge/docs-stable-blue.svg)](https://tkf.github.io/Run.jl/stable) [![Dev](https://img.shields.io/badge/docs-dev-blue.svg)](https://tkf.github.io/Run.jl/dev) [![Build Status](https://travis-ci.com/tkf/Run.jl.svg?branch=master)](https://travis-ci.com/tkf/Run.jl) [![Codecov](https://codecov.io/gh/tkf/Run.jl/branch/master/graph/badge.svg)](https://codecov.io/gh/tkf/Run.jl) [![Coveralls](https://coveralls.io/repos/github/tkf/Run.jl/badge.svg?branch=master)](https://coveralls.io/github/tkf/Run.jl?branch=master) [![GitHub last commit](https://img.shields.io/github/last-commit/tkf/Run.jl.svg?style=social&logo=github)](https://github.com/tkf/Run.jl)

Run.jlは、隔離された環境でテストを実行したり、ドキュメントをビルドするための関数を提供します。詳細は[ドキュメント](https://tkf.github.io/Run.jl/dev)を参照してください。

## 機能

  * よりシンプルなCIセットアップ（`.travis.yml`、`.gitlab-ci.yml`など）
  * Julia < 1.2のための隔離可能でアクティベート可能なサブ環境
  * テストだけでなく、任意のサブプロジェクト（ドキュメント、ベンチマークなど）に対して再現可能な実行
  * より細かいJuliaオプション（例：`Run.test(fast=true)`でJITコンパイルを最小限に抑えてテストを高速化）

## 例

### `.github/workflow/*.yml`

以下は、GitHub ActionsでRun.jlを使用するための例です。例えば、`.github/workflow/test.yml`というファイルを作成し、次の内容を記述します。

```yaml
name: Run tests

on:
  push:
    branches:
      - master
    tags: '*'
  pull_request:

jobs:
  test:
    runs-on: ubuntu-latest
    strategy:
      matrix:
        julia-version: ['1']
      fail-fast: false
    name: Test Julia ${{ matrix.julia-version }}
    steps:
      - uses: actions/checkout@v2
      - name: Setup julia
        uses: julia-actions/setup-julia@v1
        with:
          version: ${{ matrix.julia-version }}
      - run: julia -e 'using Pkg; pkg"add Run@0.1"'
      - run: julia -e 'using Run; Run.prepare_test()'
      - run: julia -e 'using Run; Run.test()'
      - uses: julia-actions/julia-processcoverage@v1
      - uses: codecov/codecov-action@v1
        with:
          file: ./lcov.info
          flags: unittests
          name: codecov-umbrella
```

### `.travis.yml`

Travis CIでテストを実行するために`Run.test`を使用するには、`.travis.yml`に次のスニペットを追加します。

```yaml
before_install:
  - unset JULIA_PROJECT
  - julia -e 'using Pkg; pkg"add Run@0.1"'
install:
  - julia -e 'using Run; Run.prepare_test()'
script:
  - julia -e 'using Run; Run.test()'
after_success:
  - julia -e 'using Run; Run.after_success_test()'
jobs:
  include:
    - stage: Documentation
      install:
        - julia -e 'using Run; Run.prepare_docs()'
      script:
        - julia -e 'using Run; Run.docs()'
      after_success: skip
```

補足:

  * `Run.prepare_test()`および`Run.prepare_docs()`は必須ではありませんが、インストールとテストを分けるのは良い考えです。
  * テストログは、`Run.test`に`prepare=false`を渡すことで最小限に抑えることができます。

### `.gitlab-ci.yml`

```yaml
.template:
  image: julia
  before_script:
    - julia -e 'using Pkg; pkg"add Run@0.1"'

test:
  extends: .template
  script:
    - julia -e 'using Run; Run.test()'

pages:
  extends: .template
  stage: deploy
  script:
    - julia -e 'using Run; Run.docs()'
    - mv docs/build public
  artifacts:
    paths:
      - public
  only:
    - master
```
