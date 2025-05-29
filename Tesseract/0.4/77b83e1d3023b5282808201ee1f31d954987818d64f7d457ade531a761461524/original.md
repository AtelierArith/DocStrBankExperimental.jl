```
pix_delete!(
    pix::Pix
)::Nothing
```

Release the Pix object so it can be freed.

**Arguments:**

|   T | Name | Default | Description           |
| ---:|:---- |:------- |:--------------------- |
|   R | pix  |         | The image to release. |

**Details:**

This method is called automatically by the garbage collector but can be called manually to release the object early.  This method can be called multiple times without any negative effects.

Calling this method will free the object unless a reference is held by an external library.  Once that library releases it's reference the Pix object should be fully freed.  However once `pix_delete!()` is called on an object passing the object to any other library call will result in an error.

Note: This method is not thread safe.
