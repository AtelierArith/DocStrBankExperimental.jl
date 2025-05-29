```julia
two_stage_estimation(
    estset::MomentMatching.EstimationSetup,
    auxmomsim::MomentMatching.AuxiliaryParameters,
    Nseeds::Integer,
    Nsamplesim::Integer,
    Ndata::Integer;
    aux,
    npmm,
    saving,
    saving_bestmodel,
    filename_suffix,
    errorcatching
)

```

二段階推定手続き。

# 必要な引数

  * estset: EstimationSetupのインスタンス。別のドキュメントを参照してください [`EstimationSetup`](@ref)。
  * npmomsim: モデルと推定されたパラメータが正しいと仮定したときにモーメントの分布をシミュレートするために使用される数値パラメータを含みます。その形式は制限されていませんが、`defaultInnerAuxStructure(mode,npmomsim)`は有効なaux構造を返す必要があります。元のモーメントが計算されたデータを生成するプロセスを模倣する必要があります。
  * nprepeat: 異なるモーメントを一致させるためにモデルのパラメータを再推定する際に使用される数値パラメータを含みます。その形式は制限されていませんが、`defaultInnerAuxStructure(mode,npmomsim)`は有効なaux構造を返す必要があります。元の推定のセットアップを模倣する必要があります。
  * Nseeds: 各代替サンプルモーメントベクトルに対して試す異なるシードの数。
  * Nsamplesim: 試す代替サンプルモーメントベクトルの数。
  * Ndata: データサンプルのサイズ。

# オプションの引数

  * npmm: 推定のための数値パラメータ。別のドキュメントを参照してください [`NumParMM`](@ref)。
  * saving_est: 論理値、推定結果を保存する場合はtrue。
  * saving_bestmodel: 論理値、最良のパラメータに対応するモデル解にリンクされたオブジェクトを保存する場合。
  * filename_suffix: 保存時にファイル名に使用されるサフィックスを含む文字列。
