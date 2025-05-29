```julia
@def_sim sim_name default_type_params begin
    obs_typedef
end
```

シミュレーション内の単一観測の型定義（`obs_typedef`）が与えられた場合、その型定義をそのまま評価しますが、`sim_name`という名前の2番目の型も作成し、新しい型に対してさまざまなメソッドを定義します。

`sim_name`のフィールドは`obs_typedef`のフィールドと同じ名前を持ちますが、対応する`obs_typedef`フィールドの型の配列になります。`sim_name`は配列の構造体であることを意図しています（https://en.wikipedia.org/wiki/AOS*and*SOAを参照）。構造体の配列が必要な場合は、単に`obs_typedef`で定義された型のインスタンスの配列を収集してください。配列の構造体ストレージ形式は、特定の値のすべてのフィールドではなく、特定のフィールドのすべての値を一度に操作したい場合に、キャッシュ効率とデータの局所性が向上します。

新しい型`sim_name`に加えて、次のメソッドが定義されます：

  * `sim_name(sz::NTuple{N,Int})`。これは、各フィールドのサイズ`sz`の配列を割り当てる`sim_name`のコンストラクタです。`obs_typedef`に型パラメータが含まれている場合、デフォルト値（`default_type_params`で指定されたもの）が使用されます。
  * `Base.endof(::sim_name)`：そのフィールドのいずれかの長さに等しい
  * `Base.length(::sim_name)`：そのフィールドのいずれかの長さに等しい
  * `sim_name`のイテレータプロトコル。イテレータの各要素の型は`obs_typedef`で定義された型です。これは次のメソッドを定義することに相当します

      * `Base.start(::sim_name)::Int`
      * `Base.next(::sim_name, ::Int)::Tuple{Observation,Int}`
      * `Base.done(::sim_name, ::Int)::Bool`
  * `Base.getindex(sim::sim_name, ix::Int)`。これは`sim_name`の*線形インデックス*を実装し、`obs_typedef`で定義された型のインスタンスを返します。

## 例

注意：`using MacroTools`と`MacroTools.prettify`への呼び出しは必要なく、出力をクリーンアップして読みやすくするためにのみ使用されています。

```
julia> using MacroTools

julia> macroexpand(:(@def_sim Simulation (T => Float64,) struct Observation{T<:Number}
           c::T
           k::T
           i_z::Int
       end
       )) |> MacroTools.prettify
quote
    struct Simulation{prairiedog, T <: Number}
        c::Array{T, prairiedog}
        k::Array{T, prairiedog}
        i_z::Array{Int, prairiedog}
    end
    function Simulation{prairiedog}(sz::NTuple{prairiedog, Int})
        c = Array{Float64, prairiedog}(sz)
        k = Array{Float64, prairiedog}(sz)
        i_z = Array{Int, prairiedog}(sz)
        Simulation(c, k, i_z)
    end
    struct Observation{T <: Number}
        c::T
        k::T
        i_z::Int
    end
    Base.endof(sim::Simulation) = length(sim.c)
    Base.length(sim::Simulation) = endof(sim)
    Base.start(sim::Simulation) = 1
    Base.next(sim::Simulation, ix::Int) = (sim[ix], ix + 1)
    Base.done(sim::Simulation, ix::Int) = ix >= length(sim)
    function Base.getindex(sim::Simulation, ix::Int)
        $(Expr(:boundscheck, true))
        if ix > length(sim)
            throw(BoundsError("$(length(sim))-element Simulation at index $(ix)"))
        end
        $(Expr(:boundscheck, :pop))
        $(Expr(:inbounds, true))
        out = Observation(sim.c[ix], sim.k[ix], sim.i_z[ix])
        $(Expr(:inbounds, :pop))
        return out
    end
end
```
