# 関数呼び出し

`par(z...)`

# 説明

これはインピーダンスの並列接続を計算します。オプションとして、計算はモジュールUnitfulの単位を使用して行うことができます。

関数`par`と`∥`は冗長な実装です。

# 変数

`z` インピーダンスのベクトル

# 例

```julia
julia> using Unitful,Unitful.DefaultSymbols,ElectricalEngineering
julia> par(4,6)
2.4
julia> par(4Ω,6Ω)
2.4 Ω

```

`\Omega`と入力して`tab`キーを押すと、並列記号Ωがオートコンプリートされます。
