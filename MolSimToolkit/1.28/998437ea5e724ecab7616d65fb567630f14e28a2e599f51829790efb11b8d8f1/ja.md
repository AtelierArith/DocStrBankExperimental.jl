```
Simulation(pdb_file::String, trajectory_file::String; frames=[1,2,3,5])
Simulation(pdb_file::String, trajectory_file::String; frames=9:2:20)
Simulation(pdb_file::String, trajectory_file::String; first=1, last=nothing, step=1)
Simulation(atoms::AbstractVector{<:AtomType}, trajectory_file::String; first=1, last=nothing, step=1)
```

新しい `Simulation` オブジェクトを作成します。

最初のコンストラクタは、PDB または mmCIF ファイルとトラジェクトリファイルから `Simulation` オブジェクトを作成します。これは、`PDBTools.Atom` を原子タイプとして使用し、`Simulation` オブジェクトの `atoms` ベクターを埋めます。現在、他の原子タイプもサポートされていますが、原子タイプに対して `MolSimToolkit.atomic_mass(::AtomType)` 関数が定義されている必要があります。

2 番目のコンストラクタでは、`atoms` ベクターが引数として渡されます。これは、原子が PDB ファイルとは異なるソースから提供される場合に便利です。

`frames` または `first`、`last`、`step` 引数を使用して、反復処理するフレームを指定できます：

```
- `frames` はフレームインデックスのベクターであることができます。例：`frames=[1,2,3,5]` または `frames=9:2:20`。
- `first`、`last`、および `step` は、反復処理するフレームを指定する整数です。
  `last` が指定されていない場合、トラジェクトリの最後のフレームが使用されます。
```

`Simulation` オブジェクトは、トラジェクトリファイルと原子の PDB データを含みます。トラジェクトリ内のフレームを取得するために反復処理できます。`Simulation` オブジェクトは可変構造体で、次のデータを含み、対応する関数によって取得できます：

  * `frame_range(::Simulation)`: 反復処理するフレームのリスト
  * `frame_index(::Simulation)`: トラジェクトリ内の現在のフレームのインデックス
  * `length(::Simulation)`: 現在の範囲を考慮したトラジェクトリファイル内の反復処理するフレームの数
  * `raw_length(::Simulation)`: トラジェクトリファイル内のフレームの数
  * `atoms(::Simulation)`: シミュレーション内の原子

`Simulation` オブジェクトは、次の関数によっても操作できます：

  * `close(::Simulation)`: トラジェクトリファイルを閉じる
  * `restart!(::Simulation)`: トラジェクトリファイルの反復処理を再開する
  * `first_frame!(::Simulation)`: トラジェクトリファイルの反復処理を再開し、現在のフレームをトラジェクトリの最初のフレームに置く
  * `current_frame(::Simulation)`: トラジェクトリ内の現在のフレームを返す
  * `next_frame!(::Simulation)`: トラジェクトリファイル内の次のフレームを読み込み、それを返す。現在のフレームを次のフレームに移動する。
  * `set_frame_range!(::Simulation; first, last, step)`: 反復処理するフレームの範囲をリセットする。
  * `get_frame(::Simulation, iframe)`: トラジェクトリ内の指定されたインデックスのフレームを返す。

`Simulation` オブジェクトの重要な機能の一つは、フレームごとに反復処理できることです。

`pairs` イテレータを使用してフレームを反復処理することもでき、フレームインデックスとフレーム自体のタプルを返します。

`enumerate` イテレータを使用してフレームを反復処理することもでき、フレームカウンタとフレーム自体のタプルを返します。

# 例

```julia-repl # to be doctest
julia> using MolSimToolkit, MolSimToolkit.Testing

julia> simulation = Simulation(
           Testing.namd_pdb, Testing.namd_traj; 
           first = 2, step = 2, last = 4,
           # または frames = [2,4]
       );

julia> for frame in simulation 
           @show frame_index(simulation)
           # 最初の原子の x 座標を表示 
           @show positions(frame)[1].x
       end
frame_index(simulation) = 2
((positions(frame))[1]).x = 5.912472724914551
frame_index(simulation) = 4
((positions(frame))[1]).x = 7.346549034118652

julia> for (i, frame) in pairs(simulation)
           @show i, frame_index(simulation)
       end
(i, frame_index(simulation)) = (2, 2)
(i, frame_index(simulation)) = (4, 4)  

julia> for (i, frame) in enumerate(simulation)
           @show i, frame_index(simulation)
       end
(i, frame_index(simulation)) = (1, 2)
(i, frame_index(simulation)) = (2, 4)

```
