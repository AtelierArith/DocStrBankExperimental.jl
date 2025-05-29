ParticleID

  * 著者: F.Gaede, DESY

# フィールド

  * `type::Int32`: ユーザー定義型
  * `PDG::Int32`: このIDのPDGコード - 不明な場合は ( 999999 )。
  * `algorithmType::Int32`: この仮説を作成したアルゴリズム/モジュールのタイプ
  * `likelihood::Float32`: この仮説の尤度 - ユーザー定義の正規化で。
  * `parameters::PVector{Float32}`: この仮説に関連付けられたパラメータ。インデックスをデコードするためのコレクションパラメータ ParameterNames_PIDAlgorithmTypeName を確認/設定してください。

# メソッド

  * `setParameters(object::ParticleID, v::AbstractVector{Float32})`: `parameters` ベクターメンバーに値のセットを割り当てる
