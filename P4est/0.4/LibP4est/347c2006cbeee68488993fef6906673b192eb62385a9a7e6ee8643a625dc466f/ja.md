```
p4est_inspect
```

選択、検査、およびプロファイリングアルゴリズムに関するデータ。この構造体へのポインタは、`p4est`のメイン構造体にフックされています。

balance*rangesおよびbalance*notify*の時間は、`p4est`にinspect構造体が存在するたびに収集されます。

| フィールド                     | 注釈                                                                                        |
|:------------------------- |:----------------------------------------------------------------------------------------- |
| use*balance*ranges        | 非対称通信パターンを決定するためにsc*rangesを使用します。*use*balance*ranges*がfalse（デフォルト）である場合、sc*notifyが使用されます。 |
| use*balance*ranges_notify | trueの場合、sc*rangesとsc*notifyの両方を呼び出し、一貫性を確認します。実際に使用されるのは*use*balance*ranges*によって決まります。    |
| use*balance*verify        | 適用可能なsc*rangesおよび/またはsc*notifyを検証します。                                                     |
| balance*max*ranges        | 正の値であり、p4est_num rangesより小さい場合、それを上書きします。                                                 |
| balance_ranges            | sc_rangesに費やした時間                                                                          |
| balance_notify            | sc_notifyに費やした時間                                                                          |
| balance*notify*allgather  | sc*notify*allgatherに費やした時間                                                                |
