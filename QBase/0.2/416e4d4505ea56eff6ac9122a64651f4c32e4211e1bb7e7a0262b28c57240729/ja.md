```
base_n_val(
    num_array :: Vector{Int64},
    base :: Int64;
    big_endian=true :: Bool
) :: Int64
```

n進数を表す配列を与えると、その数の10進数での値を返します。

入力:

  * `num_array` - 基数未満の半正整数を含むベクター。
  * `base` - num_arrayによって表されるn進数。
  * `big_endian` - 最上位桁がインデックス1にある場合は`true`、そうでない場合は`false`。
