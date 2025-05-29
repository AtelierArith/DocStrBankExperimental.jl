```
fixed_point(func::Function, previous_FixedPointResults::FixedPointResults;
                Algorithm::Symbol = :Anderson,  ConvergenceMetric::Function  = supnorm(input::Array, output::Array) = maximum(abs.(output .- input)),
                ConvergenceMetricThreshold::R = 1e-10, MaxIter::Integer = Integer(1000), MaxM::Integer = Integer(10), ExtrapolationPeriod::Integer = Integer(7), Dampening::Real = AbstractFloat(1.0),
                PrintReports::Bool = false, ReportingSigFig::Integer = Integer(10), ReplaceInvalids::Symbol = :NoAction, ConditionNumberThreshold::Real = 1e3, quiet_errors::Bool = false) where R<:Real
fixed_point(func::Function, Inputs::Array{T, 1};
                Algorithm::Symbol = :Anderson,  ConvergenceMetric::Function  = supnorm(input::Array, output::Array) = maximum(abs.(output .- input)),
                ConvergenceMetricThreshold::Real = 1e-10, MaxIter::Integer = Integer(1000), MaxM::Integer = Integer(10), ExtrapolationPeriod::Integer = Integer(7), Dampening::Real = AbstractFloat(1.0),
                PrintReports::Bool = false, ReportingSigFig::Integer = Integer(10), ReplaceInvalids::Symbol = :NoAction, ConditionNumberThreshold::Real = 1e3, quiet_errors::Bool = false) where T<:Real
fixed_point(func::Function, Inputs::Real;
                Algorithm::Symbol = :Anderson,  ConvergenceMetric::Function  = supnorm(input::Array, output::Array) = maximum(abs.(output .- input)),
                ConvergenceMetricThreshold::Real = 1e-10, MaxIter::Integer = Integer(1000), MaxM::Integer = Integer(10), ExtrapolationPeriod::Integer = Integer(7), Dampening::Real = AbstractFloat(1.0),
                PrintReports::Bool = false, ReportingSigFig::Integer = Integer(10), ReplaceInvalids::Symbol = :NoAction, ConditionNumberThreshold::Real = 1e3, quiet_errors::Bool = false)
fixed_point(func::Function, Inputs::Array{T, 2}; Outputs::Array{T,2} = Array{T,2}(undef,size(Inputs)[1],0),
                Algorithm::Symbol = :Anderson,  ConvergenceMetric::Function  = supnorm(input::Array, output::Array) = maximum(abs.(output .- input)),
                ConvergenceMetricThreshold::Real = 1e-10, MaxIter::Integer = Integer(1000), MaxM::Integer = Integer(10), ExtrapolationPeriod::Integer = Integer(7), Dampening::Real = AbstractFloat(1.0),
                PrintReports::Bool = false, ReportingSigFig::Integer = Integer(10), ReplaceInvalids::Symbol = :NoAction, ConditionNumberThreshold::Real = 1e3, quiet_errors::Bool = false, other_outputs::Union{Missing,NamedTuple} = missing) where T<:Real where R<:Real
```

他の関数の固定点を見つけるための関数

### 入力

  * `func` - これは固定点を求める関数です。この関数は同じサイズのベクトルを受け取り、返す必要があります。
  * `Inputs` - これは固定点の初期推測である1Dベクトルの値であるか、対応する出力が利用可能な以前の入力のN x A行列であることができます。この場合、Nは求めている固定点ベクトルの次元（したがって各列はfへの入力行列）であり、Aは固定点に提供される以前の入力/出力の数です。行列が入力される場合、対応する出力が提供される必要があります。そうでない場合、出力行列の最後の列がスタートポイントの推測として取られ、他の入力および出力行列は破棄されます。
  * `Outputs` - これは入力の各列に対する関数値の行列です。出力行列の列kは入力行列の列kに等しくなるように提供される必要があります。
  * `Algorithm` - これは使用する固定点アルゴリズムです。:Anderson、:Simple、:Aitken、:Newton、:MPE、:RRE、:VEA、または:SEAのいずれかです。これらのアルゴリズムの説明については、ドキュメントおよび参考文献を参照してください。
  * `ConvergenceMetric` - これは入力ベクトルと出力テーブルを受け取り、スカラーを返す関数です。このスカラーは収束が近づくと低くなるべきです。デフォルトでは、これは絶対値による最大残差（残差空間におけるsupノルム）です。
  * `ConvergenceMetricThreshold` - これはアルゴリズムを終了するための閾値です。ConvergenceMetricが返すスカラーがConvergenceMetricThresholdより小さい場合、アルゴリズムは終了します。これは負の数に設定することができ、その場合、アルゴリズムはMaxIterに達するか、エラーが発生するまで実行されます（固定点がすでに見つかっている場合、"Simple"以外のアルゴリズムを使用しようとするとエラーが発生する可能性が高いことに注意してください）。
  * `MaxIter` - これは実行される最大の反復回数です。
  * `MaxM` - これはAndersonアルゴリズムで使用される保存された反復の最大数です。他のアルゴリズムが選択された場合、影響はありません。実際に使用される以前の反復の数は、MaxIter、fのベクトルの次元、および以前に試みられた入力の数（アルゴリズムの各段階での出力行列の幅）の最小値です。PrintReports = TRUEの場合、実際に使用された以前の反復の数がアルゴリズムの実行中に報告されます。
  * `ExtrapolationPeriod` - これは外挿を行う前に実行する単純な反復の数です。これはMPE、RRE、VEA、およびSEAアルゴリズムで使用され、他のアルゴリズムが選択された場合は影響がありません。イプシロンアルゴリズムが使用される場合、これは2の倍数であるべきです（例：4、6、8など）。
  * `Dampening` - これはダンピングパラメータです。デフォルトでは1で、これはダンピングが行われないことを意味します。1未満（ダンピングを示す）または1より大きい（外挿を示す）こともできます。
  * `PrintReports` - これは各反復の進行中のConvergenceMetric値を印刷するかどうかを示すブール値です。
  * `ReportingSigFig` - これは収束値をコンソールに印刷する際に使用される有効数字の数です（PrintReportsがTRUEの場合のみ）。
  * `ReplaceInvalids` - 時々、加速アルゴリズムが無効な座標（NaN、Inf、または欠損）を持つベクトルを提案します。このパラメータは、無効な座標を単純な反復値で置き換えるために:ReplaceInvalidsに設定することができます、全体のベクトルを単純な反復で置き換えるために:ReplaceVectorに設定することができます、または差し迫ったエラーが発生する場合は:NoActionに設定することができます。
  * `ConditionNumberThreshold` - これはAndersonアルゴリズムの最小二乗問題を解決するために受け入れ可能な条件数の閾値です。この条件数がこの閾値を超えると、問題を解決するために使用される以前の反復が少なくなります。:Andersonアルゴリズムが使用されていない限り、影響はありません。
  * `quiet_errors` - trueの場合、関数はエラーが発生するとすぐにすでに計算されたすべてを返します。ただし、エラーにつながったコールスタックは返されません。falseの場合、エラーがスローされ、コールスタックが表示されます。
  * `other_outputs` - これは副産物を渡すことを可能にします（FixedPointResults構造体のOther*Output*のように）。これは、入力されたFixedPointResultsがすでに固定点を見つけた場合にのみ使用されます。

### 戻り値

  * `FixedPointResults`構造体が返され、固定点、入力、および対応する出力、収束値（これは"ConvergenceMetric"の下で計算されます）が含まれます。このリストには、終了理由を説明する"Finish"ステートメントも含まれます。これは、MaxIterまたはConvergenceMetricThresholdに達したためであることが多いです。また、新しい入力推測を生成する際のエラーや、その推測を使用して関数を使用することによるエラーで終了することもあります。この場合、関数は早期に終了し、"Finish"ステートメントが問題を説明します。この場合、デバッグに役立つ"NewInputVector"およびおそらく"NewOutputVector"という追加のオブジェクトもリストに返されます。

### 例

```
# 最も単純な例として、スカラーでcos関数の固定点を求めることができます。
Inputs = 0.3
Func(x) = cos(x)
A = fixed_point(Func, Inputs; Algorithm = :Aitken, Dampening = 0.5)
B = fixed_point(Func, Inputs; Algorithm = :Anderson, Dampening = 1.0)

# 次の例では、ConvergenceMetricThresholdが負であるため、アルゴリズムは
# MaxIterに達するまで実行され続けます。
C = fixed_point(Func, Inputs; Algorithm = :Simple, MaxIter = 4, ConvergenceMetricThreshold = -1.0)
# しかし、今度はニュートンアルゴリズムに切り替えてこの固定点を解き続けることができます。
D = fixed_point(Func, C[:Inputs], C[:Outputs]; Algorithm = :Newton)

# この関数の4次元固定点ベクトルを見つけることもできます。
Inputs = [0.3, 98, 0, pi]
E = fixed_point(Func, Inputs; Algorithm = :Anderson)
F = fixed_point(Func, Inputs; Algorithm = :Anderson, MaxM = 4, ReportingSigFig = 13)
```
