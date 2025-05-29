```
ReverseSequence(dim = nothing)
```

渡された配列の指定された次元 `dims` を逆にします

## 引数

  * `dim`: 逆にする必要がある次元。`nothing` の場合、AbstractVector{T} は自分自身を逆にします（次元 1）、他の配列の場合は次元 `ndims(x) - 1` を逆にします。

## 入力

  * `x`: AbstractArray。

## 戻り値

  * 入力と同じ次元を持つ AbstractArray
  * 空の `NamedTuple()`

## 例

```jldoctest
julia> model = ReverseSequence()
ReverseSequence{Nothing}(nothing)

julia> rng = Random.default_rng();
       Random.seed!(rng, 0);
       ps, st = Lux.setup(rng, model);
       x = [1.0, 2.0, 3.0];

julia> y, st_new = model(x, ps, st)
([3.0, 2.0, 1.0], NamedTuple())
```
