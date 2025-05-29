```
sc_list_reset(list)
```

リストからすべての要素をO(N)で削除します。

!!! note
    [`sc_list_init`](@ref)を呼び出し、その後に任意のリスト操作を行い、次に[`sc_list_reset`](@ref)を呼び出すことはメモリに中立です。


### パラメータ

  * `list`:[in,out] 空にするリスト構造体。

### プロトタイプ

```c
void sc_list_reset (sc_list_t * list);
```
