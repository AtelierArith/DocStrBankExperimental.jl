```
@enum StateCategory
```

状態のタイプ。

| 値         | 説明                                 |
|:--------- |:---------------------------------- |
| `XD`      | 差分変数（変数の導関数が方程式に現れる）               |
| `XALG`    | x に含まれる代数変数                        |
| `XLAMBDA` | der_x に含まれる代数変数                    |
| `XMUE`    | 安定化に使用され、der_x に含まれる代数変数（正確な値 = 0） |
