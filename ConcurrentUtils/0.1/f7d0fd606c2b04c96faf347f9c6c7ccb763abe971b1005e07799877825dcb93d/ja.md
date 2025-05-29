# ConcurrentUtils: Juliaのための並行プログラミングツール

[![Dev](https://img.shields.io/badge/docs-dev-blue.svg)](https://juliaconcurrent.github.io/ConcurrentUtils.jl/dev/) [![CI](https://github.com/JuliaConcurrent/ConcurrentUtils.jl/actions/workflows/test.yml/badge.svg)](https://github.com/JuliaConcurrent/ConcurrentUtils.jl/actions/workflows/test.yml)

ConcurrentUtils.jlは、`Base.Threads`ライブラリを補完するために、Juliaにおける並行計算のための高レベルおよび低レベルのプログラミングツールを提供します。高レベルAPIには以下が含まれます：

  * [`Promise{T}`](https://juliaconcurrent.github.io/ConcurrentUtils.jl/dev/#ConcurrentUtils.Promise): 一度設定され、非同期に取得できる型`T`の値を保持するメモリ位置。
  * [`@tasklet code`](https://juliaconcurrent.github.io/ConcurrentUtils.jl/dev/#ConcurrentUtils.@tasklet): `Promise`のようなメモ化されたサンク。
  * [`@once code`](https://juliaconcurrent.github.io/ConcurrentUtils.jl/dev/#ConcurrentUtils.@once): `code`を最大1回実行します。
  * [`ReadWriteLock`](https://juliaconcurrent.github.io/ConcurrentUtils.jl/dev/#ConcurrentUtils.ReadWriteLock): リーダー-ライターロック。
  * ... さらに多く

詳細は[Documentation](https://juliaconcurrent.github.io/ConcurrentUtils.jl/dev/)を参照してください。
