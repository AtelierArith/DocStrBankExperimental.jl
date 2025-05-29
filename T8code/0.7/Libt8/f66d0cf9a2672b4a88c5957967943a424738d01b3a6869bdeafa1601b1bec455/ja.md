```
t8_element_new(ts, length, elems)
```

指定されたクラスの要素の配列のメモリを割り当て、初期化します。

!!! note
    t8codeで作成されるすべての要素がこの関数の呼び出しによって作成されるわけではありません。ただし、要素がt8*element*newを使用して作成されていない場合、t8*element*initがその要素に対して呼び出されることが保証されます。


!!! note
    デバッグモードでは、t8*element*newで作成された要素はt8*element*is_validを通過しなければなりません。


!!! note
    要素がt8*element*newによって作成された場合、t8*element*initはその要素に対して呼び出されない可能性があります。したがって、t8*element*newはt8*element*initの呼び出しと同じ方法で要素を初期化する必要があります。


# 引数

  * `ts`:[in] クラススキームの実装。
  * `length`:[in] 割り当てる要素の数。
  * `elems`:[in,out] 入力時には**length**個の未割り当て要素ポインタの配列。出力時には、これらのポインタはすべて割り当てられ、初期化された要素を指します。

# 参照

t8*element*init, t8*element*is_valid

### プロトタイプ

```c
void t8_element_new (const t8_eclass_scheme_c *ts, int length, t8_element_t **elems);
```
