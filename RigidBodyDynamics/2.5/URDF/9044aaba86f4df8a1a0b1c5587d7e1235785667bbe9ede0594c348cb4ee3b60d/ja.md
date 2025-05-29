```julia
parse_urdf(
    filename;
    scalar_type,
    floating,
    joint_types,
    root_joint_type,
    remove_fixed_tree_joints,
    gravity,
    revolute_joint_type,
    floating_joint_type
)

```

[URDF](https://wiki.ros.org/urdf/XML/model) ファイルを解析して `Mechanism` を作成します。

キーワード引数:

  * `scalar_type`: `Mechanism` の運動学的および慣性特性を格納するために使用されるスカラー型。デフォルト: `Float64`。
  * `floating`: ルートジョイントとして浮動ジョイントを使用するかどうか。デフォルト: false。
  * `joint_types`: URDF ジョイントタイプ名を `JointType` サブタイプにマッピングする辞書。デフォルト: [`default_urdf_joint_types()`](@ref)。
  * `root_joint_type`: 解析された `Mechanism` を世界に接続するために使用される `JointType` インスタンス。デフォルト: `floating` の場合は浮動 URDF ジョイントタイプタグに対応するジョイントタイプのインスタンス、そうでない場合は固定 URDF ジョイントタイプタグのジョイントタイプのインスタンス。
  * `remove_fixed_tree_joints`: 運動学的ツリーに存在する固定ジョイントを [`remove_fixed_tree_joints!`](@ref) を使用して削除するかどうか。デフォルト: `true`。
  * `gravity`: `Mechanism` のルートフレームで表現された 3 ベクトルとしての重力加速度。デフォルト: `[0.0, 0.0, -9.81]`。
