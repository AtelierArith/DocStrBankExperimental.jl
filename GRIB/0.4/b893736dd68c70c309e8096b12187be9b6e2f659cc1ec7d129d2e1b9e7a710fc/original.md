```
Nearest(f::Function, handle::Message)
```

Create a Nearest from a Message and automatically destroy when finished.

# Example

```Julia
Nearest(handle) do near
    find(near, handle, inlat, inlon)
end
```
