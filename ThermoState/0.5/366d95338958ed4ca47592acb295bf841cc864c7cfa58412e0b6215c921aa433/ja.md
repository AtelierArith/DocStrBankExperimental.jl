```
amount_type(st::ThermodynamicState)
```

与えられた状態に基づいて、物質の量がどのように指定されているかに関する情報を含むタプルを返します。

タプルの最初の要素は、状態に存在する成分の数に関連しています。成分が1つだけの場合は `SingleComponent` を返します。複数成分の仕様（`MaterialCompounds`）が定義されている場合は、そのタイプを返します。

2番目の要素は、指定された材料のタイプ（モルまたは質量）に関連しています。仕様がない場合は、1モルを仮定し、タイプ `OneMol` を返します。指定されている場合は `MaterialAmount` を返します。

## 例

```julia-repl
julia> tp = state(t=1,p=2)
ThermodynamicState with 2 properties:
  Temperature : 1[K]
  Pressure : 2[Pa]

julia> amount_type(tp)
(SingleComponent(), OneMol())

julia> tpn = state(t=1,p=2,mass=3)
ThermodynamicState with 3 properties:
  Temperature : 1[K]
  Pressure : 2[Pa]
  Mass : 3[kg]

julia> amount_type(tpn)
(SingleComponent(), MaterialAmount{MASS}())

julia> tpxm = state(t=1,p=2,mass=3,xn = [0.1,0.9])      
ThermodynamicState with 4 properties:
  Temperature : 1[K]
  Pressure : 2[Pa]
  Mass : 3[kg]
  Molar fraction : [0.1, 0.9]

julia> amount_type(tpxm)
(MaterialCompounds{MOLAR, FRACTION}(), MaterialAmount{MASS}())

julia> tpm = state(t=1,p=2,m = [1,2])
ThermodynamicState with 3 properties:
  Temperature : 1[K]
  Pressure : 2[Pa]
  Mass amounts : [1, 2][kg]

julia> amount_type(tpm)
(MaterialCompounds{MASS, TOTAL_AMOUNT}(), MaterialCompounds{MASS, TOTAL_AMOUNT}())
```
