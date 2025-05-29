`@like(type)` は、Julia の型をその共変形状型に変換します。OO 型 `Cls` の orm が `[Cls, Base1, Base2]` の場合、対応する共変形状型は `@like(Cls) == Object{U} where U >: Union{Cls, Base1, Base2}` です。
