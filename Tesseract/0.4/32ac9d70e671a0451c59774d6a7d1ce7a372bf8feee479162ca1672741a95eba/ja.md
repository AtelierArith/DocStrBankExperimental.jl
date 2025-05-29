```
mutable struct TessInst
    ptr::Ptr{Cvoid}
end
```

TesseractライブラリのApiオブジェクトのラッパーです。

**値:**

| 名前  | 説明                                |
|:--- |:--------------------------------- |
| ptr | Cライブラリによって割り当てられたApiオブジェクトへのポインタ。 |

**詳細:**

ほとんどのメソッド呼び出しは、初期化のために`tess_init()`が呼ばれるまでこのオブジェクトを使用できません。

ガーベジコレクタがこのオブジェクトを収集すると、関連するポインタオブジェクトはライブラリ内で解放されます。このオブジェクトは、`tess_delete!()`を呼び出すことで手動で解放することもできます。

参照: [`TessInst(languages::AbstractString, dataPath::AbstractString)`](@ref)。
