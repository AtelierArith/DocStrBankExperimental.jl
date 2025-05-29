```
autodiff_thunk(::ReverseModeSplit, ftype, Activity, argtypes::Type{<:Annotation}...)
```

注釈付き関数型 `ftype` のための分割前方および逆方向パス関数を提供します。これは、逆モードを使用して `argtypes` 型の引数で呼び出されたときのものです。

`Activity` は戻り値のアクティビティであり、`Const`、`Active`、または `Duplicated`（またはその変種である `DuplicatedNoNeed`、`BatchDuplicated`、`BatchDuplicatedNoNeed`）のいずれかです。

前方関数はテープ、プライマル（または要求されていない場合は何も）、およびシャドウ（または `Duplicated` 変種でない場合は何も）を返し、提供された対応する型引数をテープします。

逆関数は `Active` 引数の導関数を返し、`Duplicated` 引数をその場で更新します。前方パスに対して同じ引数を提供し、次に戻り値の随伴（戻り値がアクティブな場合）を提供し、最後に前方パスからのテープを提供します。

例：

```jldoctest

A = [2.2]; ∂A = zero(A)
v = 3.3

function f(A, v)
    res = A[1] * v
    A[1] = 0
    res
end

forward, reverse = autodiff_thunk(ReverseSplitWithPrimal, Const{typeof(f)}, Active, Duplicated{typeof(A)}, Active{typeof(v)})

tape, result, shadow_result  = forward(Const(f), Duplicated(A, ∂A), Active(v))
_, ∂v = reverse(Const(f), Duplicated(A, ∂A), Active(v), 1.0, tape)[1]

result, ∂v, ∂A 

# 出力

(7.26, 2.2, [3.3])
```
