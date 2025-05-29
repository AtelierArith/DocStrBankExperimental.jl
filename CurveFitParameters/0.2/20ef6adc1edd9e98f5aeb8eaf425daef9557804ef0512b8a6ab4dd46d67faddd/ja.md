モデルパラメータのセットの型 - `OrderedDict{String, Parameter}`をラップします。`AbstractDict`インターフェースを実装しています。単一の`Parameter`には`params.name`または`params["name"]`を介してアクセスできます。

# コンストラクタ:

```
Parameters()
```

空のパラメータセットを構築します。

```
Parameters(x::AbstractVector{<:Real}, names::AbstractVector{<:AbstractString}, lower_bounds=nothing, upper_bounds=nothing, vary=nothing)
```

`Vector`からパラメータのセットを構築します。
