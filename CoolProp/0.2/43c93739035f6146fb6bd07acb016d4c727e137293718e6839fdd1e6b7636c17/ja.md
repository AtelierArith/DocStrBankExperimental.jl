```
set_config(key::AbstractString, val::AbstractString)
```

設定文字列を設定します。

# 引数

  * `key::AbstractString`: 設定するキー。以下の表に可能な `key` の値、そのデフォルト設定、およびその使用法を示します。
  * `val::AbstractString`: キーに設定する値

| キー                               | デフォルト | 説明                                                                                        |
|:-------------------------------- |:-----:|:----------------------------------------------------------------------------------------- |
| ALTERNATIVE*TABLES*DIRECTORY     |  ""   | 提供された場合、このパスは表形式データのルートディレクトリになります。そうでない場合、:({HOME})/.CoolProp/Tables が使用されます             |
| ALTERNATIVE*REFPROP*PATH         |  ""   | REFPROPの流体および混合物ディレクトリを含むディレクトリへの代替パス。提供された場合、SETPATH関数はREFPROP関数を呼び出す前にこのディレクトリで呼び出されます。 |
| ALTERNATIVE*REFPROP*HMX*BNC*PATH |  ""   | HMX.BNCファイルへの代替パス。提供された場合、REFPROPのSETUPまたはSETMIXルーチンに渡されます                                |
| VTPR*UNIFAC*PATH                 |  ""   | UNIFAC JSONファイルを含むディレクトリへのパス。スラッシュで終わる必要があります                                             |
