```
@dfcc(method="svd-dcsd")
```

密度適合積分を使用して結合クラスター計算を実行します。

メソッドのタイプは最初の引数によって決まります。メソッドは文字列または変数として指定できます。例えば、`@dfcc SVD-DCSD` または `@dfcc "SVD-DCSD"` または `ccmethod="SVD-DCSD";  @dfcc ccmethod`。

# 例

```julia
geometry="bohr
O      0.000000000    0.000000000   -0.130186067
H1     0.000000000    1.489124508    1.033245507
H2     0.000000000   -1.489124508    1.033245507"
basis = Dict("ao"=>"cc-pVDZ", "jkfit"=>"cc-pvtz-jkfit", "mpfit"=>"cc-pvdz-mpfit")
@dfhf
@dfcc svd-dcsd
```
