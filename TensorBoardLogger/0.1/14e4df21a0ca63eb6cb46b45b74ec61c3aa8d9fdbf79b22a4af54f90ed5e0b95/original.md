log*image(logger, name, obj; [step=current*step])

Renders the object to PNG and sends it to TensorBoard as an image with tag `name`. `showable("image/png", obj)` must be true.
