```
witness_set(F; codim = nvariables(F) - length(F), dim = nothing, options...)
```

与えられた次元（またはコディメンション）で `F` の [`WitnessSet`](@ref) を計算します。ランダムな（アフィン）線形部分空間をサンプリングします。システムを構築した後、提供された `options` で [`solve`](@ref) を呼び出します。

```
witness_set(F, L; options...)
```

`F` と（アフィン）線形部分空間 `L` のための [`WitnessSet`](@ref) を計算します。

```
witness_set(W::WitnessSet, L; options...)
```

`W` に保存されている線形部分空間を `L` に移動させることによって、（アフィン）線形部分空間 `L` を持つ新しい [`WitnessSet`](@ref) を計算します。

### 例

```julia-repl
julia> @var x y;
julia> F = System([x^2 + y^2 - 5], [x, y])
System of length 1
 2 variables: x, y

 -5 + x^2 + y^2

julia> W = witness_set(F)
Witness set for dimension 1 of degree 2
```
