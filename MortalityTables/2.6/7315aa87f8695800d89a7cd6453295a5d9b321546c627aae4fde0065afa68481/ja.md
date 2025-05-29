```
survival(mortality_vector,to_age)
survival(mortality_vector,from_age,to_age)
```

`to_age`に達した年齢までの生存を返します。計算の開始はベクトルの開始点、または達成した年齢`from_age`のいずれかです。`from_age`と`to_age`は整数である必要があります。浮動小数点数や非整数の年齢を処理するために、最後の引数として`DeathDistribution`を追加します：

```
survival(mortality_vector,to_age,::DeathDistribution)
survival(mortality_vector,from_age,to_age,::DeathDistribution)
```

負の`to_age`が与えられた場合、`1.0`を返します。コードを簡素化することに加えて、何かが存在し、最初に減少できるためには、存在し、減少できるポイントまで生存している必要があるため、これは理にかなっています。

# 例

```julia-repl
julia> qs = UltimateMortality([0.1,0.3,0.6,1]);
    
julia> survival(qs,0)
1.0
julia> survival(qs,1)
0.9

julia> survival(qs,1,1)
1.0
julia> survival(qs,1,2)
0.7

julia> survival(qs,0.5,Uniform())
0.95
```
