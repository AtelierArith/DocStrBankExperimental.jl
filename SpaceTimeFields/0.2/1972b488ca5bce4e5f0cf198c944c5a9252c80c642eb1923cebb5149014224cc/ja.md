```
FunctionProfile(f::Function)
```

指定された関数 `f` からなるプロファイルを作成します。関数は単一の引数（時間）を受け取り、単一の値を返す必要があります。

# 例

```jldoctest
julia> f(t) = 2.0*t

julia> p = SpaceTimeFields.FunctionProfile(f)
関数プロファイル

julia> p(2.0)
4.0
```
