型をパッキングするために使用されるフォーマット。

`TypeFormat`で型`T::Type`をパックおよびアンパックするには、`t = StructPack.TypeValue(T)`が機能し、`StructPack.composetype(t)`が`T`を正常に再構築できることを確認してください。

`T`に型パラメータがある場合、それらのシリアル化は[`typeparamtypes`](@ref)および[`typeparamformats`](@ref)関数を介して影響を受ける可能性があります。

デフォルトでは、すべての型パラメータは[`TypedFormat`](@ref)でパック/アンパックされます。
