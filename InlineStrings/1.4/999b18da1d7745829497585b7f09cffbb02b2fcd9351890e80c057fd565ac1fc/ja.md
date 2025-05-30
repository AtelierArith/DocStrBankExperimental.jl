```
InlineStrings.String255(str::AbstractString)
InlineStrings.String255(bytes::AbstractVector{UInt8}, pos, len)
InlineStrings.String255(ptr::Ptr{UInt8}, [len])
```

カスタム固定サイズの文字列で、サイズは256バイトです。1バイトは文字列の長さを格納するために使用されます。インライン文字列が255バイト未満の場合、全体の文字列は定義上、固定サイズであるため、フル256バイトを占有します。それ以外の場合、通常の`String`値と同様に扱うことができます。`sizeof(x)`は、`String`のようにInlineStrings.String255内の*コードユニット*の数を返し、総固定サイズは返しません。固定サイズを取得するには、`sizeof(InlineStrings.String255)`を呼び出します。InlineStrings.String255は、既存の`String`から（`InlineStrings.String255(x::AbstractString)`）、位置と長さを持つバイトバッファから（`InlineStrings.String255(buf, pos, len)`）、ポインタからオプションの長さで（`InlineStrings.String255(ptr, len)`）構築することができ、`x = InlineStrings.String255()`で始めて`x, overflowed = InlineStrings.addcodeunit(x, b::UInt8)`を呼び出すことで反復的に構築することもできます。これにより、新しいコードユニット`b`が追加された新しいInlineStrings.String255と、固定サイズのためにコードユニットが多すぎて追加されたかどうかを示す`overflowed`の`Bool`値が返されます。ポインタから構築する場合、`ptr`は有効なメモリを指している必要があり、そうでないとプログラムデータが破損する可能性があります。ポインタで`len`引数が指定されている場合、それはInlineStrings.String255の固定サイズ内に収まる必要があります。長さが提供されていない場合、C文字列はNUL終端であると見なされます。NUL終端の文字列がInlineStrings.String255に収まるよりも長くなると、ArgumentErrorがスローされます。
