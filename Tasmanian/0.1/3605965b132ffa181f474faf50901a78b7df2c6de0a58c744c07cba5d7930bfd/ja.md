```
getNeededPoints(tsg::TasmanianSG)
```

は、セット***Refinement() 呼び出しに続いて、補間子を形成するために必要なポイントまたは次のレベルの洗練に必要なポイントを返します。

出力: サイズ dimension X getNumNeeded() の 2-D 配列 各列は 1 つのポイントに対応します if (getNumNeeded() == 0): zeros(dimensions, 0) を返します
