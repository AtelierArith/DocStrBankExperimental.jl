```
trixi_include_changeprecision(T, [mod::Module=Main,] elixir::AbstractString; kwargs...)
```

`include` elixir `elixir` をモジュール `mod` のグローバルスコープで評価します。キーワード引数を指定することで、`elixir` 内の特定の割り当てを上書きすることができます。これは [`trixi_include`](@ref) と似ています。

[`trixi_include`](@ref) との唯一の違いは、含まれる elixir 内の浮動小数点数の精度が `T` に変更されることです。より正確には、パッケージ [ChangePrecision.jl](https://github.com/JuliaMath/ChangePrecision.jl) が使用され、すべての `Float64` リテラル、`Float64` 結果を生成する `/` のような演算、およびデフォルトで `Float64` 配列を返す `ones` のような関数が、希望する型 `T` に変換されます。詳細については ChangePrecision.jl のドキュメントを参照してください。

この関数の目的は、`Float32` で完全なシミュレーションを便利に実行することです。`Float32` はほとんどの GPU で `Float64` よりも桁違いに高速です。`trixi_include_changeprecision(Float32, elixir)` を使用して elixir を含めるだけで済みます。Trixi.jl フレームワークの多くのコンストラクタは、すべての浮動小数点引数を `Float32` に変更すると、要素の型も `Float32` に変更されるように書かれています。TrixiParticles.jl では、このマクロを使用して elixir を含めるだけで、単精度で完全なシミュレーションを実行するのに十分です。
