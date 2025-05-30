```
InlineStrings.String63(str::AbstractString)
InlineStrings.String63(bytes::AbstractVector{UInt8}, pos, len)
InlineStrings.String63(ptr::Ptr{UInt8}, [len])
```

カスタム固定サイズの文字列で、サイズは64バイトです。1バイトは文字列の長さを格納するために使用されます。インライン文字列が63バイト未満の場合、全体の文字列は定義上、固定サイズであるため、フルの64バイトを占有します。それ以外の場合、通常の`String`値と同様に扱うことができます。`sizeof(x)`は、`String`のようにInlineStrings.String63内の*codeunits*の数を返し、総固定サイズは返しません。固定サイズを取得するには、`sizeof(InlineStrings.String63)`を呼び出します。InlineStrings.String63は、既存の`String`から（`InlineStrings.String63(x::AbstractString)`）、位置と長さを持つバイトバッファから（`InlineStrings.String63(buf, pos, len)`）、オプションの長さを持つポインタから（`InlineStrings.String63(ptr, len)`）構築することができ、`x = InlineStrings.String63()`から始めて`x, overflowed = InlineStrings.addcodeunit(x, b::UInt8)`を呼び出すことで反復的に構築することもできます。これにより、新しいcodeunit `b`が追加された新しいInlineStrings.String63と、固定サイズのために多すぎるcodeunitsが追加されたかどうかを示す`overflowed`の`Bool`値が返されます。ポインタから構築する場合、`ptr`は有効なメモリを指している必要があり、そうでないとプログラムデータが破損する可能性があります。ポインタで`len`引数が指定されている場合、それはInlineStrings.String63の固定サイズ内に収まる必要があります。長さが提供されていない場合、C文字列はNULで終わっていると見なされます。NULで終わる文字列がInlineStrings.String63に収まるよりも長くなると、ArgumentErrorがスローされます。
