```
`status(:: AbstractStopping; list = false)`
```

アルゴリズムのステータスを返します：

異なるステータスは次のとおりです：

  * `Optimal`: 最適な解に到達しました。
  * `SubProblemFailure`
  * `SubOptimal`: 受け入れ可能な解に到達しました。
  * `Unbounded`: 現在の反復がノルムで大きすぎます。
  * `UnboundedPb`: 無限大の問題。
  * `Stalled`: 停止したアルゴリズム。
  * `IterationLimit`: アルゴリズムの反復が多すぎます。
  * `TimeLimit`: 時間制限。
  * `EvaluationLimit`: 使用されたリソースが多すぎます。すなわち、関数評価が多すぎます。
  * `ResourcesOfMainProblemExhausted`: サブストッピングの場合、メインストッピングのためのEvaluationLimitまたはTimeLimit。
  * `Infeasible`: デフォルトの返り値。何も行われない場合、問題は実行可能と見なされます。
  * `StopByUser`: ユーザーによって停止されました。
  * `DomainError`: どこかにNaNがあります。
  * `Exception`: 未処理の例外
  * `Unknwon`: Stoppingによって理由不明で停止された場合。

注意：

  * キーワード引数`list`をtrueに設定すると、すべてのステータスを含む`Array`が得られます。
  * 異なるステータスはメタのブール値に対応します。
