```
predict(input, [output_type]; options...)
```

与えられた入力、出力タイプ、およびオプションでBoltz-1予測を実行します。

# 入力タイプ

  * `AbstractString`: FASTA/YAMLファイルまたはディレクトリへのパス（バッチ処理用）。
  * `MolecularInput`: 単一の [`PyBoltz.Schema.MolecularInput`](@ref) オブジェクト。
  * `Vector{MolecularInput}`: バッチ処理用の [`PyBoltz.Schema.MolecularInput`](@ref) オブジェクトのベクター。

# 出力タイプ

デフォルトでは、生の結果は `out_dir` ディレクトリにディスクに書き込まれます（オプションを参照）。

便利のために、`output_type` を2番目の引数として提供することで手動のファイルI/Oを減らすことができます。

`output_type` が提供されると、入力として `MolecularInput` が提供された場合は単一のオブジェクトを返し、そうでない場合は `AbstractString` または `Vector{MolecularInput}` が提供された場合はベクターを返します。

以下の出力タイプがサポートされています：

  * `BioStructures.MolecularStructure`: 分子構造の豊かで堅牢な表現。
  * `ProteinChains.ProteinStructure`: 便利さのためのタンパク質構造のフラットで専門的な表現。

# オプション

## 数値オプション

  * `devices::Integer`: 使用するデバイスの数。デフォルト: 1。
  * `recycling_steps::Integer`: リサイクルステップの数。デフォルト: 3。
  * `sampling_steps::Integer`: サンプリングステップの数。デフォルト: 200。
  * `diffusion_samples::Integer`: 拡散サンプルの数。デフォルト: 1。
  * `step_scale::Float64`: 温度に関連するステップサイズ。デフォルト: 1.638。
  * `num_workers::Integer`: データローダーのワーカー数。デフォルト: 2。
  * `seed::Integer`: RNGシード; デフォルト: なし。

## 文字列オプション

  * `out_dir::String`: 予測を保存するパス。
  * `cache::String`: データとモデルをダウンロードするディレクトリ。

モジュール初期化時に作成されたScratch.jlバックのディレクトリにデフォルト設定; `clear_cache()`を呼び出してリセットします。

  * `checkpoint::String`: オプションのチェックポイントパス; デフォルト: Boltz-1モデル。
  * `accelerator::String`: 'gpu', 'cpu', または 'tpu'。デフォルト: 'gpu'。
  * `output_format::String`: 'pdb' または 'mmcif'。デフォルト: 'mmcif'。
  * `msa_server_url::String`: MSAサーバーのURL; `use_msa_server=true`が必要。
  * `msa_pairing_strategy::String`: 'greedy' または 'complete'; `use_msa_server=true`が必要。

## ブールフラグ

  * `verbose::Bool`: boltzログをstdoutに印刷するかどうか。デフォルト: true。
  * `write_full_pae::Bool`: PAEをnpzファイルにダンプします。デフォルト: true。
  * `write_full_pde::Bool`: PDEをnpzファイルにダンプします。デフォルト: false。
  * `override::Bool`: 既存の予測を上書きします。デフォルト: false。
  * `use_msa_server::Bool`: MSA生成のためにMMSeqs2サーバーを使用します。デフォルト: false。
