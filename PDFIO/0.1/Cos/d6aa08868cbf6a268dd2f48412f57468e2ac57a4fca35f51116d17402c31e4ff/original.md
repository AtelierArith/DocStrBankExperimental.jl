```
    CosObject
```

PDF is a structured document format with lots of internal data structures like dictionaries, arrays, trees. `CosObject` is the interface to access these objects and get detailed access to the objects and gather additional information. Although, defined in the COS layer, objects of these type are returned from almost all the APIs. Hence, the objects have a separate significance whether you need to use the `Cos` layer or not. Below is the object hierarchy.

```
CosObject                           Abstract
    CosNull                         Value (CosNullType)
CosString                           Abstract
CosName                             Concrete
CosNumeric                          Abstract
    CosInt                          Concrete
    CosFloat                        Concrete
CosBoolean                          Concrete
    CosTrue                         Value (CosBoolean)
    CosFalse                        Value (CosBoolean)
CosDict                             Concrete
CosArray                            Concrete
CosStream                           Concrete (always wrapped as an indirect object)
CosIndirectObjectRef                Concrete (only useful when CosDoc is available)
```

*Note*: As a reader API you may not need to instantiate any of `CosObject` types. They are normally populated as a result of parsing a PDF file. 
