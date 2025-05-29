```
autodiff_thunk(::ForwardMode, ftype, Activity, argtypes::Type{<:Annotation}...)
```

注釈付き関数型 `ftype` のためのサンク（thunk）前方モード関数を、`argtypes` 型の引数で呼び出すときに提供します。

`Activity` は戻り値のアクティビティで、`Const` または `Duplicated`（またはその変種である `DuplicatedNoNeed`、`BatchDuplicated`、`BatchDuplicatedNoNeed`）である可能性があります。

前方関数はシャドウ（または `Duplicated` の変種でない場合は何も返さない）と原始（要求された場合）を返します。

戻りの導関数と元の戻り値の両方を返す例：

```jldoctest
a = 4.2
b = [2.2, 3.3]; ∂f_∂b = zero(b)
c = 55; d = 9

f(x) = x*x
forward = autodiff_thunk(ForwardWithPrimal, Const{typeof(f)}, Duplicated, Duplicated{Float64})
∂f_∂x, res = forward(Const(f), Duplicated(3.14, 1.0))

# output

(6.28, 9.8596)
```

導関数だけを返す例：

```jldoctest
a = 4.2
b = [2.2, 3.3]; ∂f_∂b = zero(b)
c = 55; d = 9

f(x) = x*x
forward = autodiff_thunk(Forward, Const{typeof(f)}, Duplicated, Duplicated{Float64})
∂f_∂x, = forward(Const(f), Duplicated(3.14, 1.0))

# output

(6.28,)
```
