```
p4est_lid_init(input, high, low)
```

64ビットの符号なし整数を初期化します。*high*は3Dで同じインターフェースを使用するためのプレースホルダーです。

### パラメータ

  * `input`:[in,out] 初期化される[`p4est_lid_t`](@ref)へのポインタ。
  * `high`:[in] 指定された高ビットはゼロでなければなりません。
  * `low`:[in] *input*を初期化するための指定された低ビット。

### プロトタイプ

```c
void p4est_lid_init (p4est_lid_t * input, uint64_t high, uint64_t low);
```
