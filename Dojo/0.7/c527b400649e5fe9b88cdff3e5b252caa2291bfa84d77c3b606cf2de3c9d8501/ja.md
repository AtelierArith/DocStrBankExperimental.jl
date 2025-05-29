```
Mechanism{T}

多剛体システム。

origin: 原点で表されるグローバル参照フレーム
joints: JointConstraintオブジェクトのリスト
bodies: Bodyオブジェクトのリスト
contacts: ContactConstraintオブジェクトのリスト
system: 機構のグラフベースの表現
residual_entries: 線形システム残差のエントリを含む
data_matrix: シミュレーション中に固定されるパラメータ情報を含む
root_to_leaves: ルートノードから葉ノードへの接続のリスト
timestep: 時間の離散化
input_scaling: インパルスの内部使用のための入力スケーリング（デフォルト: timestep）
gravity: 重力ポテンシャルから生じる力ベクトル
μ: 補完性違反（接触の柔らかさ）
```
