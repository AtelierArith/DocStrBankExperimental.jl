```
    CDTextString
```

PDF file format structure provides two primary string types. Hexadecimal string `CosXString` and literal string `CosLiteralString`. However, these are mere binary representation of string types without having any encoding associated for semantic representation. Determination of encoding is carried out mostly by associated fonts and character maps in the content stream. There are also strings used in descriptions and other attributes of a PDF file where no font or mapping information is provided. This represents the string type in such situations. Typically, strings in PDFs are of 3 types.

1. Text string  a. PDDocEncoded string - Similar to ISO_8859-1  b. UTF-16BE strings
2. ASCII string
3. Byte string - Pure binary data no interpretation

1 and 2 can be represented by the `CDTextString`. `convert` methods are provided to translate the `CosString` to `CDTextString`

*Ref*: PDF Specification Section 7.9.2

*Note*: Internally `CDTextString` is a `String` object of julia. 
