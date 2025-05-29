```
@init_fn(fn, kind::Symbol = :parameter)
```

パラメータまたは状態の初期化関数を作成し、[`@compact`](@ref)を使用して作成されたCompact Lux Layerで使用します。

## 引数

  * `fn`: パラメータまたは状態を初期化するために使用される関数。この関数は単一の引数`rng`のみを取ります。
  * `kind`: `:parameter`に設定されている場合、初期化関数はレイヤーのパラメータを初期化するために使用されます。`:state`に設定されている場合、初期化関数はレイヤーの状態を初期化するために使用されます。

## 例

```jldoctest
julia> using Lux, Random

julia> r = @compact(w=@init_fn(rng->randn32(rng, 3, 2)),
           b=@init_fn(rng->randn32(rng, 3), :state)) do x
           @return w * x .+ b
       end;

julia> ps, st = Lux.setup(Xoshiro(0), r);

julia> size(ps.w)
(3, 2)

julia> size(st.b)
(3,)

julia> size(r([1, 2], ps, st)[1])
(3,)
```
