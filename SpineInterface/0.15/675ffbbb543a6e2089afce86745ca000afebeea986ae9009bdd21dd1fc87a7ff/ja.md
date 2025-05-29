```
(<p>::Parameter)(;<keyword arguments>)
```

引数に対するパラメータ `p` の値。

# 引数

  * `p` に関連付けられた各オブジェクトクラスには、それにちなんだ名前のキーワード引数があります。目的は、特定のオブジェクトに対する `p` の値を取得することです。
  * `p` に関連付けられた各リレーションシップクラスには、それに関与する各オブジェクトクラスにちなんだ名前のキーワード引数があります。目的は、特定のリレーションシップに対する `p` の値を取得することです。
  * `i::Int64`: 配列値の場合に取得する特定のインデックス（それ以外は無視されます）。
  * `t::TimeSlice`: 時間変動値の場合に取得する特定の時間インデックス（それ以外は無視されます）。
  * `inds`: `Map` をナビゲートするためのインデックス（それ以外は無視されます）。タプルはネストされた `Maps` をナビゲートすることに対応します。
  * `_strict::Bool`: 指定された引数に対してパラメータが指定されていない場合にエラーを発生させるか、`nothing` を返すかを示します。

# 例

```jldoctest
julia> using SpineInterface;


julia> url = "sqlite:///" * joinpath(dirname(pathof(SpineInterface)), "..", "examples/data/example.sqlite");


julia> using_spinedb(url)


julia> tax_net_flow(node=node(:Sthlm), commodity=commodity(:water))
4

julia> demand(node=node(:Sthlm))
3-element Vector{Float64}:
 21.0
 17.0
  9.0

julia> demand(node=node(:Sthlm), i=2)
17.0
```
