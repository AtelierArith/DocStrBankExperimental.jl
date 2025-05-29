写像のコペアリング：コプロダクト/プッシュアウトの普遍的性質。

型 `T` のコプロダクトを実装するには、メソッド `universal(::BinaryCoproduct{T}, ::Cospan{T})` および/または `universal(::Coproduct{T}, ::Multicospan{T})` を定義し、プッシュアウトについても同様にします。
