```
hpd(chn::Chains; alpha::Real=0.05, kwargs...)
```

`1-alpha` 確率質量を表す最高後方密度区間を返します。

これは単一の区間を返し、不連続領域の複数の区間は返しません。

# 例

```julia-repl
julia> val = rand(500, 2, 3);
julia> chn = Chains(val, [:a, :b]);

julia> hpd(chn)
HPD
  parameters     lower     upper 
      Symbol   Float64   Float64 

           a    0.0554    0.9944
           b    0.0114    0.9460
```
