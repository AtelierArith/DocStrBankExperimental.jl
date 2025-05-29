[`parsemusicxml`](@ref)と似ていますが、Julia型に変換することはありません。適切な型を使用して変換します。

# 例

```julia
xml_note = parsemusicxml_partial("""
<note>
  <grace/>
  <pitch>
    <step>G</step>
    <octave>4</octave>
  </pitch>
  <voice>1</voice>
  <type>16th</type>
  <stem>up</stem>
  <beam number="1">end</beam>
  <beam number="2">end</beam>
</note>
""")

Note(xml_note)
```
