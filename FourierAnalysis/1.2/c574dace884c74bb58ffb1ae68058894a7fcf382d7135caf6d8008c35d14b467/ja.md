```julia
(1)
function phase(z::Complex; func::Function=identity)

(2)
function phase(Z::AbstractArray{T};
                        unwrapdims::Int=0,
                        func::Function=identity) where T<:Complex

(3)
function phase(Z::TFAnalyticSignal;
                        unwrapped::Bool=false,
                        func::Function=identity)

(4)
function phase(𝐙::TFAnalyticSignalVector;
                        unwrapped::Bool=false,
                        func::Function=identity)

```

(1)

複素数の位相（引数）を返します。これは標準の [atan2](https://en.wikipedia.org/wiki/Atan2) 関数に対応しています。以下のメソッドとの構文的一貫性のために提供されています。

(2)

複素数配列 `Z` の位相を返します。通常、`Z` は解析信号を保持しており、その場合、出力は解析的（瞬時）位相です。出力は `Z` と同じサイズの実数配列です。

オプションのキーワード引数 `unwrapdims` が > 0 の場合、配列の `unwrapdims` 次元に沿ったアンラップされた位相を返します。たとえば、`Z` が行列である場合、`unwrapdims=1` を渡すと、その列に沿って独立して位相がアンラップされます。

(3)

[TFAnalyticSignal](@ref) オブジェクト `Z` の解析的（瞬時）位相を持つ実数行列を返します。出力はデータフィールド `Z.y` と同じサイズです。

オプションのキーワード引数 `unwrapped` が true の場合、解析信号の時間次元（dims=2）に沿ったアンラップされた位相を返します。

(4)

(3) と同様ですが、𝚯 内のすべての [TFAnalyticSignal](@ref) オブジェクトに対する位相行列のベクトルを返します。

~

すべてのメソッドでは、デフォルトで位相は [−π, π] の範囲で返されます。オプションのキーワード引数 `func` で関数が提供されると、それが位相に適用されます。たとえば

  * `func=x->x+π` を渡すと、位相が [0, 2π] で返されます。
  * `func=x->x/π` を渡すと、位相が [-1, 1] で返されます。
  * `func=sin` を渡すと、位相の正弦が返されます。

!!! note "Nota Bene"
    メソッド (2) で `unwrapdims` が >0 の場合、またはメソッド (3) と (4) で `unwrapped` が true の場合、関数 `func` はアンラップされた位相に適用されます。


**参照**: [`unwrapPhase`](@ref), [TFAnalyticSignal](@ref).

**例**: [`amplitude`](@ref) の例を参照してください。
