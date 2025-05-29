```julia
maximal_coordinates(
    mechanism;
    floating_joint_type,
    bodymap,
    jointmap
)

```

動的に同等の `Mechanism` を返しますが、フラットなツリー構造を持ちます：すべてのボディは浮動関節を介してルートボディに接続され、入力 `Mechanism` のツリー関節は非ツリー関節に変換されます（関節制約は `dynamics!` 内でラグランジュ乗数を使用して強制されます）。

キーワード引数：

  * `floating_joint_type::Type{<:JointType{T}}`: 各ボディとルートの間の関節に使用する浮動関節のタイプ。デフォルト: `QuaternionFloating{T}`
  * `bodymap::AbstractDict{RigidBody{T}, RigidBody{T}}`: 入力メカニズムのボディから出力メカニズムのボディへのマッピングで埋められます
  * `jointmap::AbstractDict{<:Joint{T}, <:Joint{T}}`: 入力メカニズムの関節から出力メカニズムの関節へのマッピングで埋められます

ここで `T` は `mechanism` の要素タイプです。
