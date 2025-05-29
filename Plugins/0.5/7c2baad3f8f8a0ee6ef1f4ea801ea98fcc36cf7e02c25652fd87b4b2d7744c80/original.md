```
function hooklist(plugins, hookfn)
```

Create a HookList which allows fast, inlinable call to the merged implementations of `hookfn` by the given plugins.

A plugin of type `TPlugin` found in plugins will be referenced in the resulting HookList if there is a method that matches the following signature: `hookfn(::TPlugin, ...)`
