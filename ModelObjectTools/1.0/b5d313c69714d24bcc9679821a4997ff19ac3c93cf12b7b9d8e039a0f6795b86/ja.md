modelObjectFromVector(baseType::Type, vectorInput::AbstractArray{<:Real},         fields = fieldnames(baseType))

vectorRepresentation() 関数によって作成された変換されたパラメータ値のベクトルに基づいてモデルオブジェクトを構築します。変更される特定のパラメータは fields 入力によって指定されます。他のパラメータは baseType 型のデフォルト値から取得されます。
