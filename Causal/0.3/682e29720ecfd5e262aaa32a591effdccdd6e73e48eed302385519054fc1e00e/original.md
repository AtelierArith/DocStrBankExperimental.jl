```
@defmodel name ex
```

Construts a model. The expected syntax is. 

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

Here `@nodes` and `@branches` blocks adefine the nodes and branches of the model, respectively. 
