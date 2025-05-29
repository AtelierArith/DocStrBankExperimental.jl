# アンダースコア

[![Stable Docs](https://img.shields.io/badge/docs-stable-blue.svg)](https://c42f.github.io/Underscores.jl/stable) [![Dev Docs](https://img.shields.io/badge/docs-dev-blue.svg)](https://c42f.github.io/Underscores.jl/dev) [![Build Status](https://github.com/c42f/Underscores.jl/workflows/CI/badge.svg)](https://github.com/c42f/Underscores.jl/actions?query=workflow%3ACI)

`Underscores` は、`@_` マクロを提供し、`_` *プレースホルダー* を無名関数の引数として解釈することで、クロージャを関数に渡すことができます。例えば、`@_ map(_+1, xs)` は `map(x->x+1, xs)` を意味します。

`Underscores` は、引数に名前を付けずに無名関数を書くのに便利です。これは、特に以下のようなデータ処理パイプラインに役立ちます。

```julia
@_ people |> filter(_.age > 40, __) |> map(_.name, __)
```

詳細については[ドキュメント](https://c42f.github.io/Underscores.jl/stable)を参照するか、`@_` マクロのオンラインヘルプをご覧ください。
