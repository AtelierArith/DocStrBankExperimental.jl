`@data`のコード生成、例えば、

```
@data A begin              抽象型 A end
    A1(Int, Int)     ≡     struct A1
                               _1 :: Int
end                            _2 :: Int
                           end


@data B{T}<:A begin        抽象型 B{T} <: A end
    B1(T, Int)        ≡    struct B1{T}
end                            _1 :: T
                               _2 :: Int
                           end


@data C{T}<:B{T} begin          抽象型 C{T} <: B{T} end
    C1{A, B} ::
    (A, B)=>C{Tuple{A, B}} ≡    struct C1{A, B} <: C{Tuple{A, B}}
end                                 _1 :: A
                                    _2 :: B
                                end


@data D{T}<:A begin        抽象型 D{T} <: A end
    D1(a::T)          ≡    struct D1{T} <: D{T}
end                            a :: T
                           end
```

さらに、`@data`マクロはこれらのデータ型のためのパターンマッチングを設定します。

```julia

@data S begin
    S1(Int)
end

@match S1(1) begin
    S1(x) => x == 1
end # => true
```
