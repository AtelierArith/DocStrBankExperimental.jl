インスタンスの基底クラスインスタンスを取得します。

```
@oodef mutable struct A
    a :: Int
    function new(a::Int)
        @mk begin
            a = 1
        end
    end
end

@oodef mutable struct B <: A
    b :: Int

    function new(a::Int, b::Int)
        @mk begin
            @base(A) = A(a)
            b = 1
        end
    end
end

b_inst = B(1, 2)
a_inst = get_base(b_inst, A) :: A
```
