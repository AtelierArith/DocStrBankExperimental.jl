```
sc_array
```

[`sc_array`](@ref) オブジェクトは、同じサイズの要素の動的配列を提供します。要素は0ベースのインデックスでアクセスされます。要素のアドレスは変更される可能性があります。配列の要素数 (== elem*count) は、sc*array*resize および sc*array*rewind によって変更できます。要素は sc*array*sort でソートできます。配列がソートされている場合、sc*array*bsearch で検索できます。優先度キューは pqueue*add と pqueue_pop (未テスト) で実装されています。

| フィールド      | 注釈                                                                        |
|:---------- |:------------------------------------------------------------------------- |
| elem_size  | 単一要素のサイズ                                                                  |
| elem_count | 有効な要素の数                                                                   |
| byte_alloc | 割り当てられたバイト数、またはこれがビューの場合は -(表示されたバイト数 + 1)： "+ 1" はサイズ0の配列とサイズ0のビューを区別します |
| array      | 要素を格納するための線形配列                                                            |
