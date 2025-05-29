```
blockassembler(operator, test_space, trial_space) -> assembler
```

BEM行列内のブロックを作成するための呼び出し可能なオブジェクトを返します。

この関数は、単一の境界要素行列内の複数のブロックの組み立てに共通するすべてのタスクを実行します。返り値は、次のように呼び出すことでブロックを生成するために使用できます。

```
assembler(I,J,storefn)
```

ここで、`I`と`J`はそれぞれ`test_space`と`trial_space`内のインデックスの配列であり、希望するブロックの行と列に対応します。

ブロックは圧縮形式で構築されることに注意してください。つまり、書き込まれるストアの行と列は、`I`と`J`内の位置です（`1:numfunctions(test_space)`および`1:numfunctions(trial_space)`内の位置ではありません）。特に、構築されたブロックのサイズは`(length(I), length(J))`になります。

この最後の特性により、`I`と`J`に`1:numfunctions(test_space)`および`1:numfunctions(trial_space)`の順列を供給することで、BEM行列の順列を組み立てることができます。
