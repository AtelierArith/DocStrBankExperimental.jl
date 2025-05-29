```
`compress_state!(:: AbstractState; save_matrix :: Bool = false, max_vector_size :: Int = length(stateatx.x), pnorm :: Real = Inf, keep :: Bool = false, kwargs...)`
```

compress_state!: 状態を次のルールに従って圧縮します。

  * 行列を含む場合で、save_matrixがfalseの場合、対応するエントリは*init*field(typeof(getfield(stateatx, k))に設定されます。
  * 長さがmax*vector*sizeを超えるベクトルを含む場合、対応するエントリはそのpnormノルムを含むサイズ1のベクトルに置き換えられます。
  * keepがtrueの場合、kwargsで指定されたエントリのみが保存されます（他のエントリは*init*field(typeof(getfield(stateatx, k))に設定されます）。
  * keepがfalseで、Stateのエントリがkwargsリストにある場合、それは可能であれば*init*field(typeof(getfield(stateatx, k))として設定されます。

参照: `copy`, `copy_compress_state`, `ListofStates`
