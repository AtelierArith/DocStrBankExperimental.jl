```
visualise!(m::Model, d::Data; controller=nothing, trajectories=nothing, resolution=nothing)
```

`Model`と`Data`のインスタンスによって指定されたMuJoCoモデルのインタラクティブな視覚化を開始します。

ビジュアライザーには、受動的ダイナミクスを視覚化したり、コントローラーをインタラクティブに実行したり、記録された軌道を再生したりするための3つの「モード」があります。受動的ダイナミクスモードは常に利用可能ですが、コントローラーモードと軌道モードは以下のキーワード引数によって指定されます。

ビジュアライザーを実行した後、`F1`を押すと、ターミナルに利用可能なマウス/ボタンオプションが表示されるヘルプが表示されます。モード間を切り替えるには、`CTRL+RightArrow`と`CTRL+LeftArrow`（またはMacの場合は`CMD`）を使用します。異なるビジュアライザーモードは次のように順序付けられています：

1. コントローラーモード（`controller`キーワードが提供されている場合）
2. 軌道モード（`trajectories`キーワードが提供されている場合）
3. 受動モード（常に利用可能）

# キーワード

  * `controller`: 各タイムステップで呼び出されるコールバック関数で、シグネチャは`controller(m, d)`です。システムに制御入力を適用する（または好きな他の操作を行う）ために使用されます。
  * `trajectories`: 単一の軌道または軌道の`Vector`で、各軌道はサイズが`(nx, T)`の`AbstractMatrix`であり、`nx = model.nq + model.nv + model.na`、`T`は軌道の長さです。各軌道は異なる長さを持つことができます。
  * `resolution`: 特定の初期ウィンドウ解像度で、ビデオの録画に便利です。これを何も設定しないと、画面サイズの2/3のデフォルト値が使用されます。

# 例

```julia
using MuJoCo
install_visualiser() # 依存関係を一度だけインストールするために実行します
init_visualiser()    # セッションに必要な依存関係をロードします

# モデルをロードする
model, data = MuJoCo.sample_model_and_data()

# シミュレーションを実行し、軌道を記録する
T = 200
nx = model.nq + model.nv + model.na
states = zeros(nx, T)
for t in 1:T
    states[:,t] = get_physics_state(model, data)
    step!(model, data)
end

# コントローラーを定義する
function ctrl!(m,d)
    d.ctrl .= 2*rand(m.nu) .- 1
end

# ビジュアライザーを実行する
reset!(model, data)
visualise!(model, data, controller=ctrl!, trajectories = states)
```
