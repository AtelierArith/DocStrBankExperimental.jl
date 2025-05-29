```
function DLRGrid(Euv, β, rtol, isFermi::Bool; symmetry::Symbol = :none, rebuild = false, folder = nothing, algorithm = :functional, verbose = false)
function DLRGrid(; isFermi::Bool, β = -1.0, beta = -1.0, Euv = 1.0, symmetry::Symbol = :none, rtol = 1e-14, rebuild = false, folder = nothing, algorithm = :functional, verbose = false)
```

DLRグリッドを作成する

# 引数:

  * `Euv`         : スペクトル密度のUVエネルギースケール
  * `β` または `beta` : 逆温度
  * `isFermi`     : boolはフェルミオンかボソンか
  * `symmetry`    : 粒子-ホール対称 :ph、または粒子-ホール非対称 :pha、または :none
  * `rtol`        : 許容絶対誤差
  * `rebuild`     : falseに設定するとファイルからDLR基底を読み込み、trueに設定するとDLR基底をその場で再計算します
  * `folder`      : rebuildがtrueでfolderが設定されている場合、dlrGridは再構築され、指定されたフォルダに保存されます。rebuildがfalseでfolderが設定されている場合、dlrGridは指定されたフォルダから読み込まれます
  * `algorithm`   : rebuild = trueの場合、:functionalを設定して機能的アルゴリズムを使用してDLR基底を生成するか、:discreteを設定して行列アルゴリズムを使用します。
  * `verbose`     : falseはDLRGridをターミナルに印刷しない、またはtrueは印刷する
