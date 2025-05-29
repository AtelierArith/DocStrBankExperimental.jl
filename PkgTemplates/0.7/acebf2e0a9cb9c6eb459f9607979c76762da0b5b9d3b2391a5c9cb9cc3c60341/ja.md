# PkgTemplates

[![Stable](https://img.shields.io/badge/docs-stable-blue.svg)](https://juliaci.github.io/PkgTemplates.jl/stable) [![Dev](https://img.shields.io/badge/docs-dev-blue.svg)](https://juliaci.github.io/PkgTemplates.jl/dev) [![CI](https://github.com/JuliaCI/PkgTemplates.jl/actions/workflows/CI.yml/badge.svg?branch=master)](https://github.com/JuliaCI/PkgTemplates.jl/actions/workflows/CI.yml?query=branch%3Amaster) [![Codecov](https://codecov.io/gh/JuliaCI/PkgTemplates.jl/branch/master/graph/badge.svg?token=WsGRSymBmZ)](https://codecov.io/gh/JuliaCI/PkgTemplates.jl) [![Code Style: Blue](https://img.shields.io/badge/code%20style-blue-4495d1.svg)](https://github.com/invenia/BlueStyle) [![ColPrac: Contributor Guide on Collaborative Practices for Community Packages](https://img.shields.io/badge/ColPrac-Contributor%20Guide-blueviolet)](https://github.com/SciML/ColPrac)

**PkgTemplatesは、新しいJuliaパッケージを簡単に、繰り返し可能で、カスタマイズ可能な方法で作成します。**

## インストール

他の登録されたJuliaパッケージと同様に、Juliaパッケージマネージャー[Pkg](https://pkgdocs.julialang.org/)を使用してインストールします：

```jl
pkg> add PkgTemplates  # ']'を押してPkg REPLモードに入ります。
```

または

```jl
julia> using Pkg; Pkg.add("PkgTemplates")
```

## 使用法

### インタラクティブ生成

次のようにして、パッケージをインタラクティブに完全にカスタマイズできます：

```jl
using PkgTemplates
Template(interactive=true)("MyPkg")
```

これにより、オプションを選択するように促され、デフォルト設定が括弧内に表示されます。

### 手動作成

`Template`を作成するのは簡単です：

```jl
using PkgTemplates
tpl = Template()
```

キーワードなしのコンストラクタは、いくつかの既存のGit設定が存在することを前提としています（設定を表示するには`git config --list`を使用し、`git config --global`で設定します）：

  * `user.name`: あなたの本名、例：ジョン・スミス。
  * `user.email`: あなたのメールアドレス、例：john.smith@acme.corp。
  * `github.user`: あなたのGitHubユーザー名、例：john-smith。

`Template`を取得したら、それを使用してパッケージを生成します：

```jl
tpl("MyPkg")
```

ただし、さまざまなオプションやプラグインを使用してテンプレートを好みに合わせてカスタマイズすることが望ましいでしょう：

```jl
using PkgTemplates
tpl = Template(;
    dir="~/code",
    plugins=[
        Git(; manifest=true, ssh=true),
        GitHubActions(; x86=true),
        Codecov(),
        Documenter{GitHubActions}(),
    ],
)
```

---

より詳細な概要については、[ユーザーガイドのドキュメント](https://juliaci.github.io/PkgTemplates.jl/stable/user/)を参照してください。

## 貢献

問題やプルリクエストは歓迎します！新しい貢献者は、[ColPrac貢献者ガイド](https://github.com/SciML/ColPrac)を読むことを確認してください。PkgTemplatesに特有のヒントについては、[開発者ガイドのドキュメント](https://juliaci.github.io/PkgTemplates.jl/stable/developer/)を参照してください。
