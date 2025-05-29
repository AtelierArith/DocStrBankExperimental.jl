```
autodiff_deferred_thunk(::ReverseModeSplit, TapeType::Type, ftype::Type{<:Annotation}, Activity::Type{<:Annotation}, argtypes::Type{<:Annotation}...)
```

逆モードを使用して、引数の型 `argtypes` で呼び出されたときの注釈付き関数型 ftype の分割前方および逆パス関数を提供します。

`Activity` は戻り値のアクティビティであり、`Const`、`Active`、または `Duplicated`（またはその変種である `DuplicatedNoNeed`、`BatchDuplicated`、`BatchDuplicatedNoNeed`）のいずれかです。

前方関数はテープ、プライマル（または要求されていない場合は何も返さない）、およびシャドウ（または `Duplicated` 変種でない場合は何も返さない）を返し、提供された対応する型引数をテープします。

逆関数は `Active` 引数の導関数を返し、`Duplicated` 引数をその場で更新します。前方パスに対して同じ引数を提供し、次に戻り値のアジョイント（戻り値がアクティブな場合）を提供し、最後に前方パスからのテープを提供します。

例：

```jldoctest

A = [2.2]; ∂A = zero(A)
v = 3.3

function f(A, v)
    res = A[1] * v
    A[1] = 0
    res
end

TapeType = tape_type(ReverseSplitWithPrimal, Const{typeof(f)}, Active, Duplicated{typeof(A)}, Active{typeof(v)})
forward, reverse = autodiff_deferred_thunk(ReverseSplitWithPrimal, TapeType, Const{typeof(f)}, Active{Float64}, Duplicated{typeof(A)}, Active{typeof(v)})

tape, result, shadow_result  = forward(Const(f), Duplicated(A, ∂A), Active(v))
_, ∂v = reverse(Const(f), Duplicated(A, ∂A), Active(v), 1.0, tape)[1]

result, ∂v, ∂A 

# output

(7.26, 2.2, [3.3])
```
