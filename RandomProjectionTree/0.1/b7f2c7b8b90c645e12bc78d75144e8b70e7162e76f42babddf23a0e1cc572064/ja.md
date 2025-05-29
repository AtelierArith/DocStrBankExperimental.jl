# RPTreeEvent

ツリーのノードでのイベント。このイベントを保存することで、学習を行いたい場合にツリー全体に新しいデータを伝播させることができます。

FIELDS

. split : 定数 `splitDiam` または `splitProj` または `splitNull` としてコーディングされたスプリットイベント。 . diameters : 平均直径と最大直径を含むサイズ2のベクトル。 . projEvent  構造体 Union{RPTProjParams, Nothing} のフィールド。 . diamEvent  構造体 Union{RPTDiamSplit, Nothing} のフィールド。

METHODS

```
1. `function RPTreeEvent(s::Int64, diameters::Vector{Float64}, pivot::Union{RPTDiamSplit,Nothing})`
直径基準でのスプリットのためのコンストラクタ。

2. `function RPTreeEvent(s::Int64, diameters::Vector{Float64}, projData::Union{RPTProjParams, Nothing})`
    ランダムベクトルに対する投影でのスプリットのためのコンストラクタ。
    直径は常に推定されるため（スプリットの構造体は計算された直径に依存します）、
    常にコンストラクタ内に存在します。

3. `function RPTreeEvent(diameters::Vector{Float64})`
     葉での直径推定を保存するためだけに使用されるコンストラクタ。イベント splitNull と共に使用されます。
```
