```
struct Model{F,argnames,defaultnames,missings,Targs,Tdefaults,Ctx<:AbstractContext}
    f::F
    args::NamedTuple{argnames,Targs}
    defaults::NamedTuple{defaultnames,Tdefaults}
    context::Ctx=DefaultContext()
end
```

モデル評価関数の型 `F`、名前 `argnames` の引数の型 `Targs`、名前 `defaultnames` のデフォルト引数の型 `Tdefaults`、欠損引数 `missings`、および型 `Ctx` の評価コンテキストを持つ `Model` 構造体。

ここで `argnames`、`defaultargnames`、および `missings` はシンボルのタプルであり、例として `(:a, :b)` がある。`context` はデフォルトで `DefaultContext()` である。

型 `Missing` の引数はデフォルトで `missings` に含まれる。しかし、非伝統的な使用ケースでは `missings` を異なる方法で定義することができる。`missings` のすべての変数は観測値ではなくランダム変数として扱われる。

デフォルト引数は、異なる引数を持つ同じモデルのインスタンスを構築する際に内部で使用される。

# 例

```julia
julia> Model(f, (x = 1.0, y = 2.0))
Model{typeof(f),(:x, :y),(),(),Tuple{Float64,Float64},Tuple{}}(f, (x = 1.0, y = 2.0), NamedTuple())

julia> Model(f, (x = 1.0, y = 2.0), (x = 42,))
Model{typeof(f),(:x, :y),(:x,),(),Tuple{Float64,Float64},Tuple{Int64}}(f, (x = 1.0, y = 2.0), (x = 42,))

julia> Model{(:y,)}(f, (x = 1.0, y = 2.0), (x = 42,)) # 欠損の特別な定義を持つ
Model{typeof(f),(:x, :y),(:x,),(:y,),Tuple{Float64,Float64},Tuple{Int64}}(f, (x = 1.0, y = 2.0), (x = 42,))
```
