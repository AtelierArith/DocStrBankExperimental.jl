`@with resources... block` は次のようなコードを生成します：

```
let resources...
   try
       block
   finally
       close.(resources)
   end
end
```

これは `Base.close` を実装しているリソースに対して便利ですが、コールバックされたリソースオープナーはありません。
