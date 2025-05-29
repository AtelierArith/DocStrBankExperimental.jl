```
PointRecord{F,N}
```

ポイントデータレコード形式 (PDRF) `F` (通常は0から10の間) のポイントデータレコードで、`N` バイトの追加データ (通常はゼロ) が含まれています。これはASPRSの「LAS」フォーマットで定義されています。

## ポイントレコード属性

ポイントレコードの属性は、以下の関数を使用してアクセスできます。構造体フィールドに直接アクセスすることは推奨されません。すべてのPDRFで利用可能なわけではない属性もあることに注意してください。

  * 3D位置: [`coordinates`](@ref)
  * 色情報: [`color_channels`](@ref) *(PDRF 2/3/5/7のRGB、PDRF 8/10のRGB + NIR)*
  * レーザーパルスの戻り情報: [`intensity`](@ref), [`return_number`](@ref), [`return_count`](@ref), [`waveform_packet`](@ref) *(PDRF 4/5/9/10のみ)*
  * ポイントレコードの分類: [`classification`](@ref), [`is_key_point`](@ref), [`is_overlap`](@ref) *(すべてのPDRF、PDRF 0–5の分類に基づく)*, [`is_synthetic`](@ref), [`is_withheld`](@ref)
  * スキャナー/フライトパス情報: [`scan_angle`](@ref) *(PDRF 6–10の高解像度)*, [`is_left_to_right`](@ref), [`is_right_to_left`](@ref), [`is_edge_of_line`](@ref), [`scanner_channel`](@ref) *(PDRF 6–10のみ)*, [`source_id`](@ref), [`gps_time`](@ref) *(PDRF 1 & 3–10)*
  * カスタム属性: [`user_data`](@ref), [`extra_bytes`](@ref)

これらの関数はすべて似たようなシグネチャを持っています：

```
attribute([T], p::PointRecord)
attribute([T], points, inds = :)
```

属性は、単一のポイントレコード `p` から、またはコレクション `points` から1つまたは複数のインデックス `inds` (`:`がデフォルト) で読み取ることができ、後者の場合は属性値のベクトルが返されます。デフォルトでは、値は正規化された `Float64` または `Int` 値として返されるため、呼び出し元は異なるPDRFにおけるデータの保存方法の詳細を知る必要はありません。オプションの型引数 `T` を使用して、生の値が変換される整数型を指定することができます (正規化なし)、または単に `Integer` に設定して生の値を取得することができます。
