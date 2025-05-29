重みベクトルを作成し、行列 `data` に重みを付けて、合計すると列の合計が `target_populations` に等しくなるようにします。 `function_type` については Creedy 論文を参照してください。制約付きタイプのいずれかを使用する場合、出力重みは初期重みの ru 倍を超えず、rl 倍を下回らない必要があります。重みと収束に関するいくつかの追加情報を含む Dict を返します。 data : KxJ 行列で、k は観測数、J は制約数です。データセットのレイアウト方法については、Joachim Merz の「最小情報損失原則によるマイクロデータ調整」および FFB 議論ペーパー No. 10（1994年7月）を参照してください。

`data` :  `intial_weights` : K 長さのベクトル `target_populations` - J 長さのベクトル;

`upper_multiple` `lower_multiple` 最終重み/初期重みの比率の最大/最小許容値（制約付き距離関数の場合） `tol` 根を求めるための値  `max_iterations` : 収束を制御するための値

注：カイ二乗はチェック目的のために存在します。必要な場合は `do_chi_square_reweighting` を使用してください。

upper*multiple/lower*multiple 最終重み/初期重みの比率の最大/最小許容値（制約付き距離関数の場合）
