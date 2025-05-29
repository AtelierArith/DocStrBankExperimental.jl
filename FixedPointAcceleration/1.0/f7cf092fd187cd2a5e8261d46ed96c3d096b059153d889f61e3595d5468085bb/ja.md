```
fixed_point_new_input(Inputs::AbstractArray{T,2}, Outputs::AbstractArray{T,2}, Algorithm::Symbol = :Anderson;
                           MaxM::Integer = 10, SimpleStartIndex::Integer = 1, ExtrapolationPeriod::Integer = 1, Dampening::S = AbstractFloat(1),
                           ConditionNumberThreshold::R = AbstractFloat(1000), PrintReports::Bool = false, ReplaceInvalids::InvalidReplacement = :NoAction) where R<:Real where S<:Real where T<:Real
```

この関数は、fixed_point関数からの以前の入力と出力を受け取り、固定点を求めるために次に試すべきベクトルを決定します。

### 入力

  * `Inputs` - これは、対応する出力が利用可能な以前の入力のN x A行列です。この場合、Nは求められている固定点ベクトルの次元（したがって、各列は「関数」への入力となる行列）であり、Aは固定点に提供される以前の入力/出力の数です。
  * `Outputs` - これは、`Inputs`行列の各列に対する関数値の行列です。
  * `Algorithm` - これは使用される固定点アルゴリズムです。「Anderson」、「Simple」、「Aitken」、「Newton」、「MPE」、「RRE」、「VEA」、「SEA」のいずれかです。
  * `MaxM` - これは、Andersonアルゴリズムで使用される保存された反復の数です。他のアルゴリズムが使用される場合は役割を持ちません。
  * `SimpleStartIndex` - これは、アルゴリズムがジャンプなしで単純な反復を開始した入力/出力行列の列のインデックスです。これは、単純およびAndersonアルゴリズムを除くすべてのアルゴリズムで使用され、効果はありません。
  * `ExtrapolationPeriod` - これは、外挿を行う前に実行する単純な反復の数です。これはMPE、RRE、VEAおよびSEAアルゴリズムで使用され、他のアルゴリズムが選択された場合は効果がありません。
  * `Dampening` - これはダンピングパラメータです。デフォルトでは1で、ダンピングが行われないことを意味します。1未満（ダンピングを示す）または1より大きい（外挿を示す）こともできます。
  * `ConditionNumberThreshold` - これは、行列が悪条件の場合に以前の反復をドロップするために選択すべきしきい値です。Anderson加速でのみ使用されます。
  * `PrintReports` - これは、各反復の進行中のConvergenceMetric値を印刷するかどうかを示すブール値です。

### 戻り値

  * 固定点の次の推測の`Vector`。

### 例

```
FPFunction = function(x){c(0.5*sqrt(abs(x[1] + x[2])), 1.5*x[1] + 0.5*x[2])}
A = fixed_point( Function = FPFunction, Inputs = [0.3,900], MaxIter = 6, Algorithm = :Simple)
NewGuessAnderson = fixed_point_new_input(A[:Inputs], A[:Outputs], Algorithm = :Anderson)
NewGuessVEA = fixed_point_new_input(A[:Inputs], A[:Outputs], Algorithm = :VEA)
NewGuessMPE = fixed_point_new_input(A[:Inputs], A[:Outputs], Algorithm = :MPE)
NewGuessAitken = fixed_point_new_input(A[:Inputs], A[:Outputs], Algorithm = :Aitken)
```
