```
synth(problem::Problem, iterator::ProgramIterator; shortcircuit::Bool=true, allow_evaluation_errors::Bool=false, mod::Module=Main)::Union{Tuple{RuleNode, SynthResult}, Nothing}
```

問題の最大数の例を満たすプログラムを合成します。 		- problem                 - IO例を含む問題定義 		- iterator                - 使用されるイテレータ 		- shortcircuit            - 1つの失敗した例を見つけた後に評価を停止するかどうか、[synth](@ref)手続きの速度を上げるため。trueの場合、返されるスコアは実際のスコアの下限近似です。 		- allow*evaluation*errors - 評価中に例外がスローされた場合に検索がクラッシュするかどうか 		- max*time                - イテレータが実行される最大時間  		- max*enumerations        - イテレータが実行される最大反復回数  		- mod                     - Mainに存在しない文法内の関数の定義を含むモジュール

解決プログラムを表すルールノードと、そのプログラムが最適かどうかを示すsynthresultのタプルを返します。`synth`は`evaluate`を使用し、[0, 1]の範囲内のスコアを返し、そのスコアが1に達するかどうかをチェックします。達しない場合は、適切なフラグを持つこれまでの最良のプログラムを返します。
