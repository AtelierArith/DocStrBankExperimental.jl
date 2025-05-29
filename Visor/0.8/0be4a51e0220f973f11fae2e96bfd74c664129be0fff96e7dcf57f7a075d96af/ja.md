```
from_name(container::Supervised, name::AbstractString)
```

`name` で識別されるプロセスを返します。これは `container` によって監視されているか、存在しない場合は何も返しません。

プロセス名にドットが含まれている場合、ノード間の区切りとしてドットを使用して監視階層を検索しないため、便利です。
