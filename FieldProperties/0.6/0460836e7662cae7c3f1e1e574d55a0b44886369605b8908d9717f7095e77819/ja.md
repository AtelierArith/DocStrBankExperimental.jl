# FieldProperties.jl

[![Build Status](https://travis-ci.com/Tokazama/FieldProperties.jl.svg?branch=master)](https://travis-ci.com/Tokazama/FieldProperties.jl) [![codecov](https://codecov.io/gh/Tokazama/FieldProperties.jl/branch/master/graph/badge.svg)](https://codecov.io/gh/Tokazama/FieldProperties.jl)

`FieldProperties`は、Juliaの構造体に柔軟に組み込むことができるメソッド/プロパティベースのAPIを作成するためのインターフェースを提供します。これは主に`@defprop`と`@properties`の使用を通じて実現されます。これらのマクロは、メソッドの作成とそれらを具体的な型のフィールドにマッピングするのに役立ちます。
