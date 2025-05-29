```
NEB(sim::AbstractSim, init_images::TupleOrArray, frames_between_images::TupleOrArray; 
    name="NEB", spring_constant=1.0e5, driver="LLG", clib_image=-1)
```

NEBインスタンスを作成します。

# 引数

  * `sim::AbstractSim`: 相互作用を含むシミュレーションインスタンス。
  * `init_images::TupleOrArray`: 初期状態と最終状態の画像のタプルまたは配列。中間状態の画像も含めることができます。
  * `frames_between_images::TupleOrArray`: 各画像ペアの間のフレーム数を指定するタプルまたは配列。
  * `name::String="NEB"`: NEBインスタンスの名前。
  * `spring_constant::Float64=1.0e5`: NEBシミュレーションで使用されるばね定数。
  * `driver::String="LLG"`: NEBシミュレーションのドライバー。オプションは `"SD"` または `"LLG"` です。
  * `clib_image::Int=-1`: ライブラリ内の特定の画像を指定するためのオプションのパラメータ（デフォルトは -1）。

# 戻り値

提供されたパラメータで構成されたNEBインスタンス。

# 例

```julia
# メッシュと対応するパラメータを定義
mesh = FDMesh(nx=60, ny=60, nz=1, dx=2e-9, dy=2e-9, dz=2e-9, pbc="xy")
params = Dict(
    :Ms => 3.84e5,
    :A => 3.25e-12,
    :D => 5.83e-4,
    :H => (0, 0, 120 * mT)
)

# 初期状態と最終状態を定義し、init_imagesリストに格納します。
# 関数、タプル、または配列など、受け入れ可能な任意のオブジェクトを使用できます。
# init_imagesリストには、中間状態も含めることができます。
init_images = [read_vtk("skx.vts"), (0, 0, 1)]

# NEBシミュレーションで使用される画像の数を指定するための補間配列を定義します。
# 補間配列の長さは、init_imagesの長さから1を引いたものにする必要があります。
# 例えば、init_images = [read_vtk("skx.vts"), read_vtk("skx2.vts"), (0, 0, 1)] の場合、 
# 補間の長さは2、つまり補間 = [5,5] のようになります。
interpolation = [6]

# create_simメソッドを使用してSimインスタンスを作成します。
sim = create_sim(mesh; params...)

# NEBインスタンスを作成し、spring_constantを設定します。ドライバーは "SD" または "LLG" です。
neb = NEB(sim, init_images, interpolation; name="skx_fm", driver="SD")
# neb.spring_constant = 1e7

# システム全体をリラックスさせます。
relax(neb; stopping_dmdt=0.1, save_vtk_every=1000, max_steps=5000)
```
