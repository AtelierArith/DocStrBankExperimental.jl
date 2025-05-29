```julia
struct CVres <: CVresult
    cvType      :: String
    scoring     :: Union{String, Nothing}
    modelType   :: Union{String, Nothing}
    predLabels  :: Union{Vector{Vector{Vector{I}}}, Nothing} where I<:Int
    losses      :: Union{Vector{BitVector}, Nothing}
    cnfs        :: Union{Vector{Matrix{I}}, Nothing} where I<:Int
    avgCnf      :: Union{Matrix{T}, Nothing} where T<:Real
    accs        :: Union{Vector{T}, Nothing} where T<:Real
    avgAcc      :: Union{Real, Nothing}
    stdAcc      :: Union{Real, Nothing}
    z           :: Union{Real, Nothing}
    p           :: Union{Real, Nothing}
end
```

[`crval`](@ref)を呼び出すと、この構造体のインスタンスが生成されます。

**フィールド:**

`.cvTpe`は、文字列として与えられるクロスバリデーション技術のタイプです（例："10-fold"）。

`.scoring`は、計算される精度のタイプで、文字列として与えられます。これは[`crval`](@ref)を呼び出すときに制御されます。現在、*精度*と*バランスの取れた精度*がサポートされています。

`.modelType`は、クロスバリデーションを実行するために使用される機械学習モデルのタイプで、文字列として与えられます。

`.predLabels`は、予測ラベルのベクトルを保持する`f`-ベクトルの`z`整数ベクトルです。各フォールド（`f`）に対して1つのベクトルがあり、各ベクトルにはクラス（`z`）の数だけのベクトルが含まれ、それぞれが試行の予測ラベルを含んでいます。

`.losses`は、各フォールドのバイナリ損失を保持するBitVector型の`f`-ベクトルです。

`.cnfs`は、クロスバリデーションの各フォールドで得られた*混同行列*を保持する行列の`f`-ベクトルです。これらの行列は*頻度*（カウント）を保持しており、すべての要素の合計は各フォールドで使用された試行の数に等しくなります。

`.avgCnf`は、クロスバリデーションのフォールド間の比率の*平均混同行列*です。この行列は*比率*を保持しており、すべての要素の合計は1.0に等しくなります。

`.accs`は、クロスバリデーションの各フォールドで得られた*精度*を保持する実数の`f`-ベクトルです。

`.avgAcc`は、クロスバリデーションのフォールド間の*平均精度*です。

`.stdAcc`は、クロスバリデーションのフォールド間の*精度の標準偏差*です。

`.z`は、観測された平均誤差損失が指定された期待値よりも劣るという仮説のための検定統計量です。

`.p`は、上記の仮説検定のp値です。

詳細については[`crval`](@ref)を参照してください。
