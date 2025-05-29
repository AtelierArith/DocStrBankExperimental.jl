modelObjectFromVector(base, vectorInput::AbstractArray{<:Real},         fields = fieldnames(typeof(base)))

vectorRepresentation()関数によって作成された変換されたパラメータ値のベクトルに基づいてモデルオブジェクトを構築します。変更される特定のパラメータはfields入力によって指定されます。他のパラメータはbase入力から取得されます。
