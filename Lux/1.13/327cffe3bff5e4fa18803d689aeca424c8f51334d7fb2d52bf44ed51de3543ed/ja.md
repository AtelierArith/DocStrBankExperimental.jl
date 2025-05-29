```
@non_trainable(x)
```

値を非訓練可能としてマークします。これにより、通常のチェックをバイパスし、値をレイヤーの状態に配置します。

## 引数

  * `x`: 非訓練可能としてマークされる値。

## 例

```jldoctest
julia> using Lux, Random

julia> r = @compact(w=ones(3), w_fixed=@non_trainable(rand(3))) do x
           @return sum(w .* x .+ w_fixed)
       end;

julia> ps, st = Lux.setup(Xoshiro(0), r);

julia> size(ps.w)
(3,)

julia> size(st.w_fixed)
(3,)

julia> res, st_ = r([1, 2, 3], ps, st);

julia> st_.w_fixed == st.w_fixed
true

julia> res isa Number
true
```
