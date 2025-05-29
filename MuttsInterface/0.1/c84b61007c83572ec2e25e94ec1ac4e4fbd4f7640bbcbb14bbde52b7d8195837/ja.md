```
@mutt struct MyType
    fields...
end
```

*mutable-until-shared* データ型を定義するためのマクロです。mutable-until-shared 型は本質的に不変のデータ構造であり、"完成" するまで変更する柔軟性を提供し、その時点で他のタスクやコードの他の部分と共有できるようになります。

`Mutt` 型は、ユーザーが `mark_immutable!(obj)` を呼び出すまで可変構造体のように振る舞い、その後は純粋に不変の型のように振る舞います。

完全な API には以下が含まれます：

  * [`mark_immutable!(obj)`](@ref): `obj` を凍結し、将来の変更を防ぎます。
  * [`branch!(obj)`](@ref): `obj` の *mutable* な浅いコピーを作成します。
  * [`mutable_version(obj)`](@ref): `obj` の可変バージョンを返します。すでに可変であれば `obj` 自体を、そうでなければ [`branch!`ed](@ref branch!) コピーを返します。
  * [`branchactions(obj::Mutt)`](@ref): ユーザーは、分岐時に発生する必要のあるアクションを持つコールバックを自分の型に対してオーバーライドできます。

このマクロは、`S` の定義を修正して、追加の最初のパラメータ `__mutt_mutable :: Bool` を含め、値が不変になるときのランタイムでの追跡を行います。内部コンストラクタは自動的に処理されるため、この生成されたフィールドを構築する必要はありません。

例：

```julia
@mutt struct S
    x :: Int
    y
    S(x, y=x+1) = new(x,y)
end
```
