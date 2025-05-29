```
@import LongModuleName as alias
@import LongModuleName.object as alias
```

モジュール `LongModuleName` を `import` で読み込み、`alias` にバインドします。モジュール内の特定のオブジェクトにも使用できます。結果の式は大まかに次のように等価です。

```julia
baremodule $(gensym())
    import LongModuleName.object
end
const alias = $(gensym()).LongModuleName
```
