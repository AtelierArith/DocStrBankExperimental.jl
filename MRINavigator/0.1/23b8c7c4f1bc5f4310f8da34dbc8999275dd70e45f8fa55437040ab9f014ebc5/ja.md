```
params = defaultNavParams()
```

データ読み込み、ナビゲーター補正、画像再構成のためのデフォルトパラメータを定義します。

# デフォルトパラメータのオプションは

  * `slices::Union{Nothing, Vector}`    - 読み込むスライスの番号を含むベクター、nothingはすべてのスライスを意味します
  * `echoes::Union{Nothing, Vector}`    - 読み込むエコーの番号を含むベクター、nothingはすべてのエコーを意味します
  * `rep::Int`                          - 読み込む繰り返し、最初の繰り返しは0です。1つを選択することが必須です
  * `comp_sensit::Bool`                 - 参照スキャンを使用して感度マップを計算します
  * `comp_centerline::Bool`             - 脊髄ツールボックス（SCT）を使用して中心線の位置を見つけます
  * `trust_SCT::Bool`                   - SCTを信頼するか、結果を表示してユーザーのフィードバックを待ちます（julia REPLを使用）
  * `use_centerline::Bool`              - ナビゲーターに基づく補正で脊髄中心線情報を使用します
  * `corr_type::String`                 - 補正タイプ。オプション: "none", "knav", "FFT", "FFT_unwrap"
  * `FFT_interval::String`              - FFTベースのアプローチで考慮されるmm単位の間隔
  * `mask_thresh::String`               - マスキングしきい値: マスクサイズを減少させるために増加させ、拡張マスクサイズのために減少させます

# 追加の必須パラメータは

  * `path_imgData::String`              - ISMRMRD形式の画像データファイルへのパス
  * `path_refData::String`              - ISMRMRD形式の参照データファイルへのパス
  * `path_sensit::String`               - 感度マップが保存されるファイルへのパス。ファイル拡張子は.matでなければなりません
  * `path_noise::String`                - ノイズ取得が保存されるファイルへのパス。ファイル拡張子は.jld2でなければなりません
  * `path_results::String`              - 結果フォルダへのパス

# 追加のオプションパラメータは

  * `path_niftiMap::String`             - 再構成された参照データがnifti形式で保存されるファイルへのパス。ファイル拡張子は.niiでなければなりません
  * `path_centerline::String`           - 脊髄ツールボックス（SCT）中心線結果が保存されるフォルダへのパス
  * `path_physio::String`              - .mat形式の生理学的トレース記録へのパス。変数は2列のベクター（1:時間 [ms], 2:トレース）で、dataと呼ばれます。時間は1日の始まりからの秒数で表現され、画像取得の前後の時間点（少なくとも4秒）を含む必要があります。

ISMRMRDリファレンス: https://onlinelibrary.wiley.com/doi/epdf/10.1002/mrm.26089 SCTリファレンス: https://spinalcordtoolbox.com
