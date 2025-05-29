```
JavaLocalRef is a JavaRef that is meant to be used with local variables in a function call.
After the function call these references may be freed and garbage collected. See note about
JNI memory management below.

This is the default reference type returned from the JNI.

Use this with JNI.PushLocalFrame / JNI.PopLocalFrame for memory management.
Also see JNI.EnsureLocalCapacity.

The internal pointer should be deleted using JNI.DeleteLocalRef
```
