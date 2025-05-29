```
Operator(ceed::Ceed; qf, dqf=QFunctionNone(), dqfT=QFunctionNone(), fields)
```

与えられたQ関数`qf`を使用してlibCEED `CeedOperator`オブジェクトを作成し、オプションでその導関数および導関数の転置を指定します。

フィールドの配列を提供する必要があり、配列の各要素はフィールドの名前（文字列またはシンボル）、対応する要素制限、基底、およびベクトルを含むタプルです。

# 例

質量行列に関連するQデータを構築するオペレーターを作成します。

```
build_oper = Operator(
    ceed,
    qf=build_qfunc,
    fields=[
        (:J, mesh_rstr, mesh_basis, CeedVectorActive()),
        (:w, ElemRestrictionNone(), mesh_basis, CeedVectorNone()),
        (:qdata, sol_rstr_i, BasisNone(), CeedVectorActive())
    ]
)
```
