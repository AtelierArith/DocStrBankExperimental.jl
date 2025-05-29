```
spdiag(m::Integer, pair::Pair...)
```

$$
m\times m
$$

[`SparseTensor`](@ref) を次の形式のペアから構築します。

```
offset => array 
```

# 例

$$
10\times 10
$$

の三重対角行列を構築したいとします。下のオフダイアゴナルはすべて -2、対角はすべて 2、上のオフダイアゴナルはすべて 3 です。対応する Julia コードは次のとおりです。

```julia
spdiag(10, -1=>-2*ones(9), 0=>2*ones(10), 1=>3*ones(9))
```
