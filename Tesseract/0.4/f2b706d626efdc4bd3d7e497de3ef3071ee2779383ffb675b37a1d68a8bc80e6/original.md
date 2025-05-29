```
tess_delete!(
    inst::TessInst
)::Nothing
```

Destroy the Tesseract object and release any associated memory.

**Arguments:**

|   T | Name | Default | Description           |
| ---:|:---- |:------- |:--------------------- |
|   R | inst |         | The instance to free. |

**Details:**

This method is called automatically by the garbage collector but can be called manually to release the object early.  This method can be called multiple times without any negative effects.

Once `tess_delete!()` is called on an object passing the object to any other library call will result in an error.

Note: This method is not thread safe.
