```
InlineStrings.String1(str::AbstractString)
InlineStrings.String1(bytes::AbstractVector{UInt8}, pos, len)
InlineStrings.String1(ptr::Ptr{UInt8}, [len])
```

カスタム固定サイズの文字列で、サイズは2バイトです。1バイトは文字列の長さを格納するために使用されます。インライン文字列が1バイト未満の場合、全体の文字列は定義上、固定サイズであるため、フルの2バイトを占有します。それ以外の場合、通常の`String`値と同様に扱うことができます。`sizeof(x)`は、`String`のようにInlineStrings.String1内の*codeunits*の数を返し、合計の固定サイズは返しません。固定サイズを取得するには、`sizeof(InlineStrings.String1)`を呼び出します。InlineStrings.String1は、既存の`String`から（`InlineStrings.String1(x::AbstractString)`）、位置と長さを持つバイトバッファから（`InlineStrings.String1(buf, pos, len)`）、ポインタからオプションの長さで（`InlineStrings.String1(ptr, len)`）構築することができ、`x = InlineStrings.String1()`で始めて`x, overflowed = InlineStrings.addcodeunit(x, b::UInt8)`を呼び出すことで反復的に構築することもできます。これにより、新しいcodeunit `b`が追加された新しいInlineStrings.String1と、固定サイズのために多くのcodeunitsが追加されたかどうかを示す`overflowed`の`Bool`値が返されます。ポインタから構築する場合、`ptr`は有効なメモリを指している必要があり、そうでないとプログラムデータが破損する可能性があります。ポインタで`len`引数が指定されている場合、それはInlineStrings.String1の固定サイズ内に収まる必要があります。長さが提供されていない場合、C文字列はNUL終端であると見なされます。NUL終端の文字列がInlineStrings.String1に収まるよりも長くなると、ArgumentErrorがスローされます。
