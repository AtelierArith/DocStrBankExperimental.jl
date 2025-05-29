```
@chkey a b c 123

周囲のモジュールと関数名、および指定された引数からチェックポイントキーを構築します。これは、チェックポイントキーの簡単な構築を目的としています。

# 例

```

julia module MyModule

using Actors

function mykey()     a = 1     b = 2     c = 3     # 何かをする     return @chkey a b c 123 end

export mykey end # MyModule

julia> using .MyModule

julia> mykey() :MyModule*mykey*a*b*c_123

```

```
