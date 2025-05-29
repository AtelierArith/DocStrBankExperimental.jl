```
AbstractState_get_spinodal_data(handle::Clong, length::Integer, tau::Array{Float64}, dalta::Array{Float64}, m1::Array{Float64})
```

スピノダル曲線のデータを取得します。

# 引数

  * `handle`: メモリに保存されている状態クラスの整数ハンドル
  * `length`: 配列に保存されている要素の数（すべての出力は同じ長さでなければなりません）
  * `tau`: 逆縮小温度の配列へのポインタ
  * `delta`: 縮小密度の配列へのポインタ
  * `m1`: M1値の配列へのポインタ（L1=M1=0のとき、臨界点）

# 注意

エラーが発生した場合、出力配列には変更が加えられません。

# 例

julia> HEOS=AbstractState*factory("HEOS","Methane&Ethane"); julia> AbstractState*set*fractions(HEOS, [0.1, 0.9]); julia> AbstractState*build*spinodal(HEOS); julia> tau, delta, m1 = AbstractState*get*spinodal*data(HEOS, 127);

# 参照

CoolProp::AbstractState*get*spinodal*data(const long handle, const long length, double* tau, double* delta, double* M1, long* errcode, char* message*buffer, const long buffer_length);
