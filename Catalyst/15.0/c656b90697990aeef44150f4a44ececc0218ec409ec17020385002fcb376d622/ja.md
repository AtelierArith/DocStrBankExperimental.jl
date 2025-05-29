```
symmap_to_varmap(sys, symmap)
```

システムと値への`Symbol`のマップを与えると、初期条件とパラメータマッピングを渡すために使用できる対応する記号変数/パラメータへのマップを生成します。

例えば、

```julia
sir = @reaction_network sir begin
    β, S + I --> 2I
    ν, I --> R
end
subsys = @reaction_network subsys begin
    k, A --> B
end
@named sys = compose(sir, [subsys])
```

は次のようになります。

```
Model sys with 3 equations
Unknowns (5):
  S(t)
  I(t)
  R(t)
  subsys₊A(t)
  subsys₊B(t)
Parameters (3):
  β
  ν
  subsys₊k
```

*シンボル*から初期条件とパラメータマッピングを指定するには、次のようにします。

```julia
symmap = [:S => 1.0, :I => 1.0, :R => 1.0, :subsys₊A => 1.0, :subsys₊B => 1.0]
u0map  = symmap_to_varmap(sys, symmap)
pmap   = symmap_to_varmap(sys, [:β => 1.0, :ν => 1.0, :subsys₊k => 1.0])
```

`u0map`と`pmap`は、その後、さまざまな問題タイプへの入力として使用できます。

注意:

  * `symmap`内の任意の`Symbol`、`sym`は`sys`の有効なフィールドでなければなりません。すなわち、`sys.sym`は定義されている必要があります。
