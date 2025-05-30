```julia
param_bootstrap_result(
    estset::MomentMatching.EstimationSetup,
    mmsolu::MomentMatching.EstimationResult,
    auxmomsim::MomentMatching.AuxiliaryParameters,
    Nseeds::Integer,
    Nsamplesim::Integer,
    Ndata::Integer;
    cs,
    saving,
    filename_suffix,
    errorcatching
) -> Any

```

ブートストラップを実行し、関連する量を計算します。

# 必要な引数

  * estset: EstimationSetupのインスタンス。別のドキュメントを参照してください [`EstimationSetup`](@ref)。
  * mmsolu: EstimationResultのインスタンス。別のドキュメントを参照してください [`EstimationResult`](@ref)。
  * auxmomsim: モデルと推定されたパラメータが正しいと仮定したときにモーメントの分布をシミュレートするために使用される数値パラメータを含みます。その形式は制限されていませんが、`defaultInnerAuxStructure(mode,auxmomsim)` は有効なaux構造を返す必要があります。元のモーメントが計算されたデータを生成するプロセスを模倣する必要があります。
  * nprepeat: 代替モーメントを一致させるためにモデルのパラメータを再推定する際にシミュレーションで使用される数値パラメータを含みます。その形式は制限されていませんが、`defaultInnerAuxStructure(mode,auxmomsim)` は有効なaux構造を返す必要があります。元の推定のセットアップを模倣する必要があります。
  * Nseeds: 各代替サンプルモーメントベクトルに対して試す異なるシードの数。
  * Nsamplesim: 試す代替サンプルモーメントベクトルの数。
  * Ndata: データサンプルのサイズ。

# オプションの引数

  * saving: 結果を保存する場合は真の論理値。
  * filename_suffix: 保存時にファイル名に使用されるサフィックスを持つ文字列。
