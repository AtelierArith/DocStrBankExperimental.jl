```
sigt, lastpc = signature([interp::Interpreter=RecursiveInterpreter()], frame::Frame, pc::Int)
```

`frame`内で`pc`から始まるメソッドのシグネチャ型`sigt`を計算します。一般的に、`pc`は`Expr(:method, methname)`文を指すべきであり、その場合`lastpc`はシグネチャの一部である`frame`内の最終文番号（すなわち、3引数の`:method`式の上の行）です。あるいは、`pc`が3引数の`:method`式を指すこともできますが、その場合はすべての関連するSSAValuesが割り当てられている必要があります。この場合、`lastpc == pc`となります。

3引数の`:method`式が見つからない場合、`sigt`は`nothing`になります。
