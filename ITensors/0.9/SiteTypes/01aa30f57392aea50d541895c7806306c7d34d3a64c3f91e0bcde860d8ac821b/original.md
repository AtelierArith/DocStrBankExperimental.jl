OpName is a parameterized type which allows making strings into Julia types for the purpose of representing operator names. The main use of OpName is overloading the `op!` method which generates operators for indices with certain tags such as "S=1/2".

To make a OpName type, you can use the string macro notation: `OpName"MyTag"`.

To make an OpName value or object, you can use the notation: `OpName("myop")`
