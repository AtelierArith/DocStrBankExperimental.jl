```
function ACTR(;
    name="model1", 
    declarative=Declarative(), 
    imaginal=Imaginal(), 
    goal = Goal(), 
    scheduler=Scheduler(), 
    visual=nothing, 
    visual_location=nothing, 
    procedural=nothing, 
    motor=nothing, 
    visicon=init_visicon(), 
    parm_type = Parms, 
    rng = Random.default_rng(),
    parms...)
```

`ACTR` モデルオブジェクトを作成するためのコンストラクタです。

# キーワード

  * `name`: モデル名
  * `declarative`: 宣言的記憶モジュール
  * `imaginal`: 想像的記憶モジュール
  * `visual`: 視覚モジュール
  * `goal`: 目標モジュール
  * `visual_location`: 視覚位置モジュール
  * `visicon`: タスクで利用可能な VisualObjects のベクトル
  * `parms`: モデルパラメータ
  * `scheduler`: イベントスケジューラ
  * `rng': 擬似乱数生成器

# 例

```@example
using ACTRModels
parms = (noise=true, τ=-1.0)
chunks = [Chunk(;animal=:dog,name=:Sigma), Chunk(;animal=:rat,name=:Bonkers)]
declarative = Declarative(;memory=chunks)
actr = ACTR(;declarative, parms...)
```
