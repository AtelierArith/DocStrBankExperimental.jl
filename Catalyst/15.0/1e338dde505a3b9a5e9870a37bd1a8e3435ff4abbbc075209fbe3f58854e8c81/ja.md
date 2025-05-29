```
balance_reaction(reaction::Reaction)
```

指定された `Reaction` に対して、すべての可能な化学量論的にバランスの取れた `Reaction` オブジェクトのベクターを返します。

例:

```julia
t = default_t()
@species Si(t) Cl(t) H(t) O(t)
@compound SiCl4 ~ Si + 4Cl
@compound H2O ~ 2H + O
@compound H4SiO4 ~ 4H + Si + 4O
@compound HCl ~ H + Cl
rx = @reaction 1.0, SiCl4 + H2O --> H4SiO4 HCl
balance_reaction(rx) # 正確に1つの解。
```

```julia
t = default_t()
@species C(t) H(t) O(t)
@compound CO ~ C + O
@compound CO2 ~ C + 2O
@compound H2 ~ 2H
@compound CH4 ~ C + 4H
@compound H2O ~ 2H + O
rx = @reaction 1.0, CO + CO2 + H2--> CH4 H2O
balance_reaction(rx) # 複数の解。
```

```julia
t = default_t()
@species Fe(t) S(t) O(t) H(t) N(t)
@compound FeS2 ~ Fe + 2S
@compound HNO3 ~ H + N + 3O
@compound Fe2S3O12 ~ 2Fe + 3S + 12O
@compound NO ~ N + O
@compound H2SO4 ~ 2H + S + 4O
rx = @reaction 1.0, FeS2 + HNO3 --> Fe2S3O12 NO + H2SO4
brxs = balance_reaction(rx) # 解なし。
```

注意:

  * 化合物の化合物を含む反応のバランスを取ることは現在サポートされていません。
  * 反応は常に単一の解をもたらすわけではなく、無限の数の解が存在するか、全く解がない場合もあります。複数の解がある場合、すべての可能な `Reaction` オブジェクトのベクターが返されます。ただし、基質と生成物は入れ替え可能であり、現在は基質と生成物のセットを維持する線形結合を解決していません。
  * 反応がバランスを取れない場合、空の `Reaction` ベクターが返されます。
