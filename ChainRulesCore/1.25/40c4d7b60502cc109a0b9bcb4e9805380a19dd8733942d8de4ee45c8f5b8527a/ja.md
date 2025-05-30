```
ProjectTo(x)
```

`x`に対して関連する接空間に接ベクトル`dx`を射影する`ProjectTo{T}`ファンクタを返します。

多くの`Number`のサブタイプ（例えば精度を確保するため）や`AbstractArray`（例えば接ベクトルによってスパース構造が維持されることを確保するため）に対してカスタム`ProjectTo`メソッドが提供されています。未知の型に対して呼び出すと、（v1.5.0以降）単に`identity`を返すため、任意の`rrule`引数に安全に適用できます。

# 例

```jldoctest
julia> pr = ProjectTo(1.5f0)  # 実数と浮動小数点精度を保持
ProjectTo{Float32}()

julia> pr(3 + 4im)
3.0f0

julia> pd = ProjectTo(Diagonal([1,2,3]))  # 構造化行列を保持
ProjectTo{Diagonal}(diag = ProjectTo{AbstractArray}(element = ProjectTo{Float64}(), axes = (Base.OneTo(3),)),)

julia> th = @thunk reshape(1:9,3,3);

julia> pd(th) isa Thunk
true

julia> unthunk(pd(th))
3×3 Diagonal{Float64, Vector{Float64}}:
 1.0   ⋅    ⋅
  ⋅   5.0   ⋅
  ⋅    ⋅   9.0

julia> ProjectTo([1 2; 3 4]')  # 特別な構造はなく、整数は浮動小数点に昇格される
ProjectTo{AbstractArray}(element = ProjectTo{Float64}(), axes = (Base.OneTo(2), Base.OneTo(2)))
```
