抽象シリアル化コンテキスト。

コンテキストは、値のパッキングとアンパッキング時にカスタム動作を一時的に強制するために導入できます。

特に、コンテキストは、型に割り当てられるフォーマット（[`format`](@ref)を介して）や構造体のフィールドに割り当てられるフォーマット（[`valueformat`](@ref)を介して）に影響を与えることができます。また、オブジェクトがパッキング前およびアンパッキング後にどのように処理されるか（[`destruct`](@ref)および[`construct`](@ref)を介して）にも影響を与えることができます。
