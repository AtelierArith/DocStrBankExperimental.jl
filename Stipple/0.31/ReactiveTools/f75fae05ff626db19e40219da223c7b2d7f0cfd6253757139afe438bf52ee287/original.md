```julia
@event(event, expr)
```

Executes the code in `expr` when a specific `event` is triggered by a UI component.

**Usage**

Define an event trigger such as a click, keypress or file upload for a component using the @on macro. Then, define the handler for the event with @event.

**Examples**

Keypress:

```julia
@app begin
  @in n = 1
end

@event :keypress begin
    println("The Enter key has been pressed")
end

ui() =  textfield(class = "q-my-md", "Input", :input, hint = "Please enter some words", @on("keyup.enter", :keypress))

@page("/", ui)
```

html output

```html
<q-input hint="Please enter some words" v-on:keyup.enter="function(event) { handle_event(event, 'keypress') }" label="Input" v-model="input" class="q-my-md"></q-input>
```

File upload:

```julia
@app begin
  @in n = 1
end

@event :uploaded begin
    println("Files have been uploaded!")
end

ui() = uploader("Upload files", url = "/upload" , method="POST", @on(:uploaded, :uploaded), autoupload=true)

route("/upload", method=POST) do
    # process uploaded files
end

@page("/", ui)
```

html output

```html
<q-uploader url="/upload" method="POST" auto-upload v-on:uploaded="function(event) { handle_event(event, 'uploaded') }">Upload files</q-uploader>
```

Finalizer:

```julia
@event :finalize begin
    @info "Calling special finalizers"
    # do your cleanup
    # ...
    # then call the default finalizer
    notify(__model__, Val(:finalize))
end
```
