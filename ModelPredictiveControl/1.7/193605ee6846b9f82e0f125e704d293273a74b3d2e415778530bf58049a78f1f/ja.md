```
setname!(model::SimModel; u=nothing, y=nothing, d=nothing, x=nothing) -> model
```

`model`の入力`u`、出力`y`、擾乱`d`、および状態`x`の名前を設定します。

キーワード引数`u`、`y`、`d`、および`x`は文字列のベクトルでなければなりません。文字列はプロット関数で使用されます。

# 例

```jldoctest
julia> model = setname!(LinModel(tf(3, [10, 1]), 2.0), u=["\$A\$ (%)"], y=["\$T\$ (∘C)"])
LinModel with a sample time Ts = 2.0 s and:
 1 manipulated inputs u
 1 states x
 1 outputs y
 0 measured disturbances d
```
