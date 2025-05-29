```
@defmodel name ex
```

モデルを構築します。期待される構文は次のとおりです。

```
    @defmodel mymodel begin 
        @nodes begin 
            label1 = Component1()
            label2 = Component1()
                ⋮
        end
        @branches begin 
            src1 => dst1 
            src2 => dst2 
                ⋮
        end
    end
```

ここで `@nodes` と `@branches` ブロックは、それぞれモデルのノードとブランチを定義します。
