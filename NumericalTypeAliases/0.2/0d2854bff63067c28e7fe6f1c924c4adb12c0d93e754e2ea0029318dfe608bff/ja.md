`NumericalTypeAliases.jl`のメインモジュールは、数値配列型エイリアスのJuliaパッケージです。

このモジュールは、`NumericalTypeAliases.jlパッケージ`で使用されるすべての型エイリアスとユーティリティをエクスポートします。

# 基本的な使い方

パッケージをインタラクティブにインストールしてインポートするには、次のようにします。

```julia-repl
julia> ]
(@v1.9) pkg> add NumericalTypeAliases
```

次に、次のように数値エイリアスを使用してパッケージを開発します。

```julia
using NumericalTypeAliases

function do_something(data::RealMatrix, labels::IntegerVector)
    # 2-D浮動小数点行列と整数ベクトルを必要とする関数を書きます。
end
```

# インポート

次の名前は、パッケージによって依存関係としてインポートされます。

  * `Base`
  * `Core`
  * `DocStringExtensions`
  * `Pkg`

# エクスポート

次の名前はエクスポートされ、パッケージを`using`したときに利用可能です。

  * [`Float`](@ref)
  * [`IntegerArray`](@ref)
  * [`IntegerMatrix`](@ref)
  * [`IntegerVector`](@ref)
  * [`NTA_ABSTRACT_TYPES`](@ref)
  * [`NTA_CONCRETE_TYPES`](@ref)
  * [`NTA_TYPES`](@ref)
  * [`NTA_VERSION`](@ref)
  * [`RealArray`](@ref)
  * [`RealFP`](@ref)
  * [`RealMatrix`](@ref)
  * [`RealVector`](@ref)
