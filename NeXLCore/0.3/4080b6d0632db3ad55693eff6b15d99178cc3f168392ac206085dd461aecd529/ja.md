```
遷移
```

内殻と外殻を表し、X線遷移を説明します。デフォルトの線重みデータベースに従って、1つ以上の元素が特性X線を持つ遷移のみがサポートされています（重み > 0 が1つ以上のZに対して）。この構造には、特性X線を指定するために必要な元素情報は含まれていません。

データ項目：

```
innerShell::SubShell
outerShell::SubShell
```

例：

```
tr1 = Transition(n"K1",n"L3")
tr2   = Transition(SubShell(1),SubShell(4))
@assert tr1==tr2
```
