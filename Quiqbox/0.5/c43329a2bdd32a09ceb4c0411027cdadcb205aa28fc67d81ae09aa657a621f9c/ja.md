```
runHFcore(HTtype, scfConfig, Ns, Hcore, HeeI, S, X, C0, maxStep, earlyStop, saveTrace, 
          printInfo=false, infoLevel=2) -> 
Tuple{Tuple{Vararg{HFtempVars}}, Bool}
```

`runHFcore`の別のメソッドで、同じ戻り値を持ちますが、より多くの基礎データを引数として取ります。

=== 位置引数 ===

`HTtype::Val{HFT} where HFT`: ハートリー–フォック法のタイプ。利用可能な`HFT`の値は:RHF, :UHFです。

`scfConfig::SCFconfig`: SCF反復の設定。

`Ns::NTuple{HFTS, Int} where HFTS`: 同じスピン配置を持つ電子の数。

`Hcore::AbstractMatrix{T} where T`: 電子ハミルトニアンのコアハミルトニアン。

`HeeI::AbstractArray{T, 4} where T`: 電子-電子相互作用テンソル（化学者の表記）で、クーロン相互作用と交換相関の両方を含みます。

`S::AbstractMatrix{T} where T`: 使用される基底セットの重なり行列。

`X::AbstractMatrix{T} where T`: `S`の変換行列。

`C0::NTuple{HFTS, AbstractMatrix{T}} where {HFTS, T}`: 正準スピン軌道の係数行列の初期推測。

`maxStep::Int`: 反復が収束するかどうかに関係なく許可される最大反復ステップ。

`earlyStop::Bool`: 収束法の性能が不安定または悪化した場合に、自動的に早期に終了（またはスキップ）するかどうか。

`saveTrace::NTuple{4, Bool}`: `runHFcore`の出力[`HFtempVars`](@ref)にすべての反復ステップから中間情報を保存（プッシュ）するかどうかを決定します。その定義は、[`HFconfig`](@ref)内のフィールド`.saveTrace`と同じです。

`printInfo::Bool`: 反復ステップと結果の情報を出力するかどうか。

`infoLevel::Int`: `printInfo=true`のときに印刷される情報の詳細レベル。これが高い（絶対値が大きい）ほど、より多くの中間ステップやその他の情報が印刷されます。`infoLevel`が`5`に達すると、すべてのステップと利用可能なすべての情報が印刷されます。
