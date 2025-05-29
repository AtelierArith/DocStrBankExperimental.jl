```
struct PushforwardMeasure{F,I,M,VC<:TransformVolCorr} <: AbstractPushforward
    f :: F
    finv :: I
    origin :: M
    volcorr :: VC
end

ユーザーは `PushforwardMeasure` を直接呼び出すべきではありません。代わりに `pushfwd` を呼び出すか、メソッドを追加してください。
```
