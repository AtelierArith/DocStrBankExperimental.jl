# FieldProperties.jl

[![Build Status](https://travis-ci.com/Tokazama/FieldProperties.jl.svg?branch=master)](https://travis-ci.com/Tokazama/FieldProperties.jl) [![codecov](https://codecov.io/gh/Tokazama/FieldProperties.jl/branch/master/graph/badge.svg)](https://codecov.io/gh/Tokazama/FieldProperties.jl)

`FieldProperties` provides an interface for creating method/property based APIs that can be flexibly incorporated into Julia structures. This is predominantly accomplished through the use of `@defprop` and `@properties`. These macros help in the creation of methods and mapping them to the fields of a concrete type.
