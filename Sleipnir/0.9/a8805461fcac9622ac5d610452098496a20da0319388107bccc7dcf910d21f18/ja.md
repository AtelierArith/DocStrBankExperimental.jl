```
initialize_glaciers(
    rgi_ids::Vector{String},
    params::Parameters;
    velocityDatacubes::Union{Dict{String, String}, Dict{String, RasterStack}}=Dict(),
)
```

提供されたRGI IDとパラメータに基づいて氷河を初期化します。

# 引数

  * `rgi_ids::Vector{String}`: 初期化する氷河を表すRGI IDのベクター。
  * `params::Parameters`: シミュレーションパラメータを含む`Parameters`オブジェクト。
  * `test::Bool`: テストモードで実行するかどうかを示すオプションのブールフラグ。デフォルトは`false`。
  * `velocityDatacubes::Union{Dict{String, String}, Dict{String, RasterStack}}`: 各RGI IDに対して、データキューブへのパスまたは速度データを持つ`RasterStack`を提供する辞書。

# 戻り値

  * `glaciers::Vector{Glacier2D}`: 初期化された`Glacier2D`オブジェクトのベクター。

# 説明

この関数は以下のステップを実行します：

1. 存在しない氷河のためのファイルを生成します。
2. 提供されたRGI IDから存在しない氷河をフィルタリングします。
3. 必要に応じて氷河のための生の気候データを生成します。
4. 提供されたRGI IDとパラメータを使用して氷河を初期化します。
5. シミュレーションパラメータで`use_glathida_data`が有効になっている場合、氷河にGlaThiDaデータを割り当てます。

# エラー

  * 提供されたRGI IDのいずれにもGlaThiDaデータがない場合、エラーをスローします。

# 警告

  * すべての氷河にGlaThiDaデータが利用可能でない場合、警告を発します。

# 例

```julia
# 初期化する氷河のRGI IDのリストを宣言します
rgi_ids = ["RGI60-11.03638", "RGI60-11.01450", "RGI60-11.02346", "RGI60-08.00203"]
# 以前に指定したRGI IDとパラメータに基づいてこれらの氷河を初期化します
glaciers = initialize_glaciers(rgi_ids, params)
```
