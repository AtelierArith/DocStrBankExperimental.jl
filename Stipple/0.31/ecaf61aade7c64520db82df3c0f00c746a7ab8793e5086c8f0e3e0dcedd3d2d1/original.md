Create a js expression that is bound to a field of a vue component. Internally this is nothing than conversion to a Symbol, but it's a short version for creating symbols with spaces.

### Example

```
julia> btn("", @click("toggleFullscreen"), icon = R"is_fullscreen ? 'fullscreen_exit' : 'fullscreen'")
"<q-btn label v-on:click="toggleFullscreen" :icon="is_fullscreen ? 'fullscreen_exit' : 'fullscreen'"></q-btn>"
```

Note: For expressions that contain only variable names, we recommend the Symbol notation

```
julia> btn("", @click("toggleFullscreen"), icon = :fullscreen_icon)
"<q-btn label v-on:click="toggleFullscreen" :icon="fullscreen_icon"></q-btn>"
```
