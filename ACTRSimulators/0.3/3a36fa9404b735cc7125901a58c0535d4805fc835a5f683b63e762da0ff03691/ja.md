*AbstractTask*

タスクのための抽象型。タスクには以下のフィールドが必要です：

  * `visible`: true の場合は GUI を表示
  * `realtime`: true の場合はモデルをリアルタイムで実行
  * `speed`: リアルタイムモデル実行の速度
  * `scheduler`: イベントスケジューラへの参照

タスクにはオプションで以下のフィールドを含めることができます：

  * `screen`: 画面上の視覚オブジェクトのベクター
  * `canvas`: GUI オブジェクトコンポーネント
  * `window`: GUI のためのウィンドウ

*Example*

以下は PVT のタスクオブジェクトの例です。

```julia
mutable struct PVT{T,W,C,F1,F2} <: AbstractTask 
    n_trials::Int
    trial::Int 
    lb::Float64
    ub::Float64 
    width::Float64
    hight::Float64
    scheduler::T
    screen::Vector{VisualObject}
    canvas::C
    window::W
    visible::Bool
    realtime::Bool
    speed::Float64
end    
```

`PVT` のコンストラクタは次の通りです。

```julia
function PVT(;
    n_trials=10, 
    trial=1, 
    lb=2.0, 
    ub=10.0, 
    width=600.0, 
    height=600.0, 
    scheduler=nothing, 
    screen=Vector{VisualObject}(), 
    window=nothing, 
    canvas=nothing, 
    visible=false, 
    realtime=false,
    speed=1.0,
    )
    visible ? ((canvas,window) = setup_window(width)) : nothing
    visible ? Gtk.showall(window) : nothing
    return PVT(n_trials, trial, lb, ub, width, height, scheduler, screen, canvas, window, visible,
        realtime, speed)
end

function setup_window(width)
	canvas = @GtkCanvas()
    window = GtkWindow(canvas, "PVT", width, width)
    Gtk.visible(window, true)
    @guarded draw(canvas) do widget
        ctx = getgc(canvas)
        rectangle(ctx, 0.0, 0.0, width, width)
        set_source_rgb(ctx, .8, .8, .8)
        fill(ctx)
    end
	return canvas,window
end
```
