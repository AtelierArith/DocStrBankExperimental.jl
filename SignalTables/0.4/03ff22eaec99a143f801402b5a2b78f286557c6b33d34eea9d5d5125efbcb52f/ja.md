```
getSignalNames(signalTable; getVar=true, getPar=true, getMap=true)::Vector{String}
```

signalTableに存在する信号名の文字列ベクターを返します（独立信号名を含む）。

  * getVar=trueの場合、Var(..)変数が含まれます。
  * getPar=trueの場合、Par(..)変数が含まれます。
  * getMap=trueの場合、Map(..)変数が含まれます。
