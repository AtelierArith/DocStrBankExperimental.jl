```julia
(1)
function polar(c::Complex)

(2)
function polar(Z::AbstractArray{T}) where T<:Complex

(3)
function polar(Z::TFAnalyticSignal)

```

(1)

複素数の振幅（モジュラス）と位相（引数）を2タプルとして返します。

(2)

複素数配列 `Z` の振幅と位相を返します。通常、`Z` は解析信号を保持しており、その場合は解析的（瞬時）振幅と位相を返します。出力はデータフィールド `Z.y` と同じサイズの2つの実数配列のタプルです。

(3)

[TFAnalyticSignal](@ref) オブジェクト `Z` の解析的（瞬時）振幅と位相を返します。出力はデータフィールド `Z.y` と同じサイズの2つの実数配列のタプルです。

~

すべてのメソッドで位相は [−π, π] の範囲で返されます。

**参照**: [`amplitude`](@ref), [`phase`](@ref), [TFAnalyticSignal](@ref).

**例**: [`amplitude`](@ref) の例を参照してください。
