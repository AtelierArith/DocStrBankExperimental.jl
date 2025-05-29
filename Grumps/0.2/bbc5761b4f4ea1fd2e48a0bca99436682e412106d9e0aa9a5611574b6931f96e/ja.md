```
DataOptions(; 
    micromode   = :Hog
    macromode   = :Ant
    balance     = :micro
    σ2          = 1.0
    id          = :Grumps
)
```

このメソッドと以下に説明するメソッドは、Grumpsがデータをどのように保存し、何を保存すべきかを指定します。こちらはよりシンプルですが、柔軟性は低いです。最初の3つのオプションは、あなたが何をしているのかを知っていない限り、デフォルトのままにしておくのが最適です。**σ2**オプションはξの分散、すなわち製品レベルのモーメントにおける誤差分散です。**id**オプションは、他のデータ構造でGrumpsを拡張するために使用されます。

```
DataOptions(
    VarξInput   :: VarξInput{T},
    VarξOutput  :: VarξOutput = VarξDefaultOutput,
    micromode   :: Symbol = :Hog,
    macromode   :: Symbol = :Ant,
    balance     :: Symbol = :micro,
    id          :: Symbol = :Grumps   
)
```

このメソッドと上記に説明したメソッドは、Grumpsがデータをどのように保存し、何を保存すべきかを指定します。こちらはより複雑で柔軟性があります。**micromode**、**macromode**、および**balance**引数は、あなたが何をしているのかを知っていない限り、デフォルトのままにしておくのが最適です。**id**オプションは、他のデータ構造でGrumpsを拡張するために使用されます。**VarξInput**は、ペナルティ項の重み行列構築に使用される分散行列です。これは、すべての市場にわたる製品の数Jに対してJ×Jの行列である必要があります。**VarξInput**に対して許可される型には、UniformScaling{T}（例：1.0 * I）およびAbstractMatrix{T}（空間を節約するためにスパース行列が推奨されますが、密行列も許可されます）が含まれます。**VarξOutput**は、解の中で生成されるべきξの分散に関する仮定を示すために使用され、望ましい場合は次の段階で入力として使用できます。オプションは*VarξHomoskedastic*、*VarξHeteroskedastic*、*VarξClustering*、および*VarξUser*です。
