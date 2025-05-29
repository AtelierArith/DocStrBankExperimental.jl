```
sc_list_destroy(list)
```

O(N)でリンクリスト構造を破棄します。

!!! note
    [`sc_list_new`](@ref)でアロケータが提供されていた場合、それは破棄されません。


### パラメータ

  * `list`:[in,out] このリストのために割り当てられたすべてのメモリが解放されます。

### プロトタイプ

```c
void sc_list_destroy (sc_list_t * list);
```
