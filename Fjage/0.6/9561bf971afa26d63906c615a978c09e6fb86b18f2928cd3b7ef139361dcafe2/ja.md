`@agent` マクロは Fjage エージェントを定義するために使用されます。このマクロは `struct` 定義を受け取り、それをエージェント定義に変換します。構造体のフィールドはエージェント属性として扱われます。Fjage エージェントタイプは `Fjage.Agent` のサブタイプであり、可変です。

`struct` 定義には、`Base.@kwdef` マクロによってサポートされる初期化を含めることができます。

# 例:

```julia
using Fjage

@agent struct MyAgent
  field1::Int = 1
  field2::String = "hello"
end

abstract type SpecialAgent <: Fjage.Agent end

@agent struct MySpecialAgent <: SpecialAgent
  agentnumber::Int = 007
  licensedtokill::Bool = true
end
```
