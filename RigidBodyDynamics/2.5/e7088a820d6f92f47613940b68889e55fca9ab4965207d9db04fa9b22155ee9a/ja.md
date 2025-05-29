```julia
attach!(
    mechanism,
    predecessor,
    successor,
    joint;
    joint_pose,
    successor_pose
)

```

`successor`を`predecessor`に`joint`を使って接続します。

`successor`と`predecessor`の用語の定義については[`Joint`](@ref)を参照してください。

`Transform3D`の`joint_pose`と`successor_pose`は、`joint`が各ボディにどのように接続されているかを定義します。`joint_pose`は`predecessor`に固定された任意のフレームに対して`frame_before(joint)`を定義し、同様に`successor_pose`は`successor`に固定された任意のフレームに対して`frame_after(joint)`を定義する必要があります。

`predecessor`はすでに`Mechanism`のボディの中に存在している必要があります。

`successor`がまだ`Mechanism`の一部でない場合、それは`Mechanism`に追加されます。そうでない場合、`joint`は`Mechanism`内の非木エッジとして扱われ、実質的にループ制約が作成され、ラグランジュ乗数を使用して強制されます（再帰アルゴリズムを使用するのではなく）。
