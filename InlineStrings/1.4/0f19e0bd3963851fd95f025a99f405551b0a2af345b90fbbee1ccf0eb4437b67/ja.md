```
InlineStrings.String7(str::AbstractString)
InlineStrings.String7(bytes::AbstractVector{UInt8}, pos, len)
InlineStrings.String7(ptr::Ptr{UInt8}, [len])
```

カスタム固定サイズの文字列で、サイズは8バイトです。1バイトは文字列の長さを格納するために使用されます。インライン文字列が7バイト未満の場合、全体の文字列は定義上、固定サイズであるため、フルの8バイトを占有します。それ以外の場合、通常の`String`値と同様に扱うことができます。`sizeof(x)`は、`String`のようにInlineStrings.String7内の*codeunits*の数を返し、総固定サイズではないことに注意してください。固定サイズについては、`sizeof(InlineStrings.String7)`を呼び出してください。InlineStrings.String7は、既存の`String`（`InlineStrings.String7(x::AbstractString)`）、位置と長さを持つバイトバッファ（`InlineStrings.String7(buf, pos, len)`）、オプションの長さを持つポインタ（`InlineStrings.String7(ptr, len)`）から構築することができ、`x = InlineStrings.String7()`で始めて`x, overflowed = InlineStrings.addcodeunit(x, b::UInt8)`を呼び出すことで反復的に構築することもできます。これにより、新しいcodeunit `b`が追加された新しいInlineStrings.String7と、固定サイズのために多くのcodeunitsが追加されたかどうかを示す`overflowed`の`Bool`値が返されます。ポインタから構築する場合、`ptr`は有効なメモリを指している必要があり、そうでないとプログラムデータが破損する可能性があります。ポインタで`len`引数が指定されている場合、それはInlineStrings.String7の固定サイズ内に収まる必要があります。長さが提供されていない場合、C文字列はNULで終わっていると見なされます。NULで終わる文字列がInlineStrings.String7に収まるよりも長くなると、ArgumentErrorがスローされます。
