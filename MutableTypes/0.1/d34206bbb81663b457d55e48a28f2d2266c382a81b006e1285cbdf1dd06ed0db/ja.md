# MutableTypes

可変コアタイプは、2つの抽象タイプに基づいています。それらは次のとおりです： • MType     <: Number • MNumber   <: MType

単一フィールド'n'を持つ可変データ構造が導入されます。具体的には： • MBool     <: MType      # n::Bool • MInteger  <: MNumber    # n::Int64 • MRational <: MNumber    # n::Rational{Int64} • MReal     <: MNumber    # n::Float64 • MComplex  <: MType      # n::Complex{Float64} そのコンストラクタは型キャスティングのように見えます。例：x = MReal(2.5)。

すべての具体的な可変タイプの取得および代入のためのメソッドには次のものが含まれます： • get, set! および toString

オーバーロードされた演算子には次のものが含まれます： • MBool     ==, ≠, ! • MInteger  ==, ≠, <, ≤, ≥, >, +, -, *, ÷, %, ^ • MRational ==, ≠, <, ≤, ≥, >, +, -, *, //, / • MReal     ==, ≠, ≈, <, ≤, ≥, >, +, -, *, /, ^ • MComplex  ==, ≠, ≈, +, -, *, /, ^

すべての具体的な可変タイプに共通するメソッドには次のものが含まれます： • copy および deepcopy

すべての数値可変タイプに対するメソッドは： • abs

すべての非複素数、数値、可変タイプに対するメソッドは： • sign

MRationalタイプに対する追加のメソッドは： • numerator および denominator

MRealタイプに対する追加のメソッドは： • round, ceil, floor, cbrt または ∛, および atan(y,x)

MComplexタイプに対する追加のメソッドは： • abs2, real, imag, conj および angle

引数がMRealまたはMComplexタイプの数学関数には次のものが含まれます： • sqrt または √, sin, cos, tan, asin, acos, atan, sinh, cosh, tanh, asinh, acosh, atanh, log, log2, log10, exp, exp2 および exp10

# Note

これらのタイプに関連する演算子、メソッド、および数学関数（copyおよびdeepcopyを除く）は、それぞれのコアタイプに属するインスタンスを返します：Bool, Integer, Rational, Real または Complex。これは、可変フィールドをそれ以外は不変のデータ構造に組み込むことを許可するために意図されているためです。したがって、そのようなフィールドは値を変更する可能性を持つことができます。不変データ構造に属する可変フィールドは、データ構造自体の外部で単純な数学的公式にシームレスに使用できるための必要なインフラストラクチャを持っています。
