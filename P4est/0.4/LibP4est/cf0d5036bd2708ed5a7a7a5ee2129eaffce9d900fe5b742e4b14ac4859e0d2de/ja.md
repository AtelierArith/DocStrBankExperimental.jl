```
sc_array_reset(array)
```

配列のカウントをゼロに設定し、すべての要素を解放します。この関数は、ビューを新しく初期化された配列に変えます。

!!! note
    [`sc_array_init`](@ref)を呼び出し、その後に任意の配列操作を行い、次に[`sc_array_reset`](@ref)を呼び出すことはメモリに中立です。例外として、[`sc_array_init_view`](@ref)および[`sc_array_init_data`](@ref)の2つの関数は、[`sc_array_reset`](@ref)を後に呼び出す必要はありません。それでも、[`sc_array_reset`](@ref)を呼び出すことは合法です。


### パラメータ

  * `array`:[in,out] リセットされる配列構造。

### プロトタイプ

```c
void sc_array_reset (sc_array_t * array);
```
