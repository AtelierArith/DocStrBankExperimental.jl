```
abstractState_all_critical_points(handle::Clong, length::Integer, T::Array{Float64}, p::Array{Float64}, rhomolar::Array{Float64}, stable::Array{Clong})
```

与えられた組成に対してすべての臨界点を計算します。

# 引数

  * `handle`: メモリに保存された状態クラスの整数ハンドル
  * `length`: この関数に渡されるバッファの長さ
  * `T`: 温度（K）の配列へのポインタ
  * `p`: 圧力（Pa）の配列へのポインタ
  * `rhomolar`: モル密度（m^3/mol）の配列へのポインタ
  * `stable`: 臨界点が安定しているかどうかのブールフラグの配列へのポインタ（1は安定、0は不安定）

# 注意

入力のいずれかの更新呼び出しにエラーがある場合、出力配列には変更が加えられません。

# 参照

CoolProp::AbstractState*all*critical*points(const long handle, const long length, double* T, double* p, double* rhomolar, long* stable, long* errcode, char* message*buffer, const long buffer_length); ```
