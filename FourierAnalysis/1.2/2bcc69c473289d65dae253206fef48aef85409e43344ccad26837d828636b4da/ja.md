```julia
(1)
function unwrapPhase(Z::AbstractArray{T};
                                unwrapdims::Int=0) where T<:Complex

(2)
function unwrapPhase(ϴ::AbstractArray{T};
                                unwrapdims::Int=0) where T<:Real

(3)
unwrapPhase(ϴ::TFPhase) [TFPhaseオブジェクトのコンストラクタ]

(4)
unwrapPhase(𝚯::TFPhaseVector) [TFPhaseVectorオブジェクトのコンストラクタ]
```

(1)

オプションのキーワード引数 `unwrapdims` が > 0 の場合、*複素数* 配列から位相（引数）を計算し、`unwrapdims` 次元に沿ってアンラップします。そうでない場合（デフォルト）は `Z` を返します。通常、`Z` は解析信号を保持します。

(2)

オプションのキーワード引数 `unwrapdims` が > 0 の場合、[−π, π] の位相データを保持する*実数*配列を `unwrapdims` 次元に沿ってアンラップします。そうでない場合は `ϴ` を返します。

(3)

位相を時間次元に沿ってアンラップし、`ϴ` オブジェクトから他のすべてのフィールドをコピーすることで [TFPhase](@ref) オブジェクトを構築します。`ϴ.func` が `identity`（何もしない）関数と異なる場合は、代わりにエラーメッセージを返します。

(4)

(3) と同様ですが、位相がアンラップされた [TFPhase](@ref) オブジェクトを 𝚯 に保持する [TFPhaseVector](@ref) を構築します。すべての ϴ ∈ 𝚯 に対して `ϴ.func` は恒等関数でなければなりません。

アンラップされた位相は、これが [0, 2π] で表されるとき、位相の累積和として定義されます。

**例**: [`amplitude`](@ref) の例を参照してください。
