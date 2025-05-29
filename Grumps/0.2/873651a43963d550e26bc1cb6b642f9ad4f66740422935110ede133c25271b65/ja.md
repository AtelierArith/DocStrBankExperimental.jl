```
DefaultMacroIntegrator( n :: Int, T :: Type; options :: Union{Vec{Symbol}, Nothing} = nothing )
```

n回のサンプルを使用して基本的なモンテカルロ積分器を作成します。型Tは省略可能で、その場合はFloat64になります。オプションの*options*引数は、デフォルトからの2つの可能な変更を示すために使用できます。すなわち、*:randomize*はランダム化を要求するために使用でき、*:replacement*は置換を伴うランダム化を示します。両方のデフォルトはfalseです。*options*はnothingまたはシンボルのベクトルのいずれかであることに注意してください。*options*のさらに別の使い方は、重みを含む列見出しを指定することです。このシンボルは、ドローのスプレッドシート内の希望する列見出しに対応する必要があります。
