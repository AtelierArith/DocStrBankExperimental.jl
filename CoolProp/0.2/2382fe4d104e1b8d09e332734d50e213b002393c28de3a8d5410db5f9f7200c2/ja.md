```
AbstractState_get_phase_envelope_data(handle::Clong, length::Integer, T::Array{Float64}, p::Array{Float64}, rhomolar_vap::Array{Float64}, rhomolar_liq::Array{Float64}, x::Array{Float64}, y::Array{Float64})
```

与えられた混合物の組成に対する相包絡線からデータを取得します。

# 引数

  * `handle`: メモリに保存された状態クラスの整数ハンドル
  * `length`: 配列に保存されている要素の数（入力と出力の両方が同じ長さでなければなりません）
  * `T`: 温度の配列へのポインタ (K)
  * `p`: 圧力の配列へのポインタ (Pa)
  * `rhomolar_vap`: 蒸気相のモル密度の配列へのポインタ (m^3/mol)
  * `rhomolar_liq`: 液相のモル密度の配列へのポインタ (m^3/mol)
  * `x`: "液体"相の組成 (警告: バッファは少なくとも Ncomp*Npoints の長さである必要がありますが、実行時にバッファの長さを確認する方法はありません)
  * `y`: "蒸気"相の組成 (警告: バッファは少なくとも Ncomp*Npoints の長さである必要がありますが、実行時にバッファの長さを確認する方法はありません)

# 例

```julia
julia> HEOS=AbstractState_factory("HEOS","Methane&Ethane");
julia> length=200;
julia> t=zeros(length);p=zeros(length);x=zeros(2*length);y=zeros(2*length);rhomolar_vap=zeros(length);rhomolar_liq=zeros(length);
julia> AbstractState_set_fractions(HEOS, [0.2, 1 - 0.2])
julia> AbstractState_build_phase_envelope(HEOS, "none")
julia> AbstractState_get_phase_envelope_data(HEOS, length, t, p, rhomolar_vap, rhomolar_liq, x, y)
julia> AbstractState_free(HEOS)
```

# 注意

入力のいずれかの更新呼び出しにエラーがある場合、出力配列には変更が加えられません。

# 参照

CoolProp::AbstractState*get*phase*envelope*data(const long handle, const long length, double* T, double* p, double* rhomolar*vap, double* rhomolar*liq, double* x, double* y, long* errcode, char* message*buffer, const long buffer*length);
