```
AbstractFFTIndex{D}
```

配列のフーリエ変換を行うことによって構築された周波数ビンに対応する配列インデックスのスーパークラスです。これには `FFTIndex{D}` と `NormalizedFFTIndex{D}` が含まれます。

# 使用法

`AbstractFFTIndex{D}` は `CartesianIndex{D}` によってインデックス可能な任意のオブジェクトのインデックスとして機能します。`AbstractFFTIndex{D}` を `CartesianIndex{D}` に直接変換する方法はありません。なぜなら、それにはインデックスされる配列に関する情報が必要だからです。この型のインスタンスは次のように使用できます。

`AbstractFFTIndex{D}` を使用して配列にインデックスを付けることは、常に境界内アクセスであることが保証されています。

# インターフェース

型 `T<:AbstractFFTIndex{D}` に対して：

  * `AbstractFFTIndex{D}` の長さは常に `D` です。
  * 型コンストラクタは `Tuple{Vararg{Integer}}` を受け入れる必要があります。入力から型パラメータを推論するコンストラクタを定義することをお勧めします。これにより、`T(x::Vararg{Integer,D})` が自動的に定義されます。
  * `Tuple(::T)` は定義されるべきで、インデックスを `NTuple{D,Int}` として返します。
  * `convert(::Type{<:FFTIndex}, ::T)` は定義されるべきです。これは、正規化因子に関する情報をエンコードする型が、一般的なインデクシングメソッドで使用される `FFTIndex` に変換されることを許可するためです。これにより、`(::Type{<:FFTIndex})(::T)` も自動的に定義されます。

Julia 1.10 以降の `CartesianIndex{D}` のように、`AbstractFFTIndex{D}` はスカラー型です。そのコンポーネントを反復処理するには、`Tuple` コンストラクタを使用して `Tuple` に変換します。
