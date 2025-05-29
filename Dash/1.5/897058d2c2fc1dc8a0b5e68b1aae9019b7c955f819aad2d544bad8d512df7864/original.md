```
dcc_logoutbutton(;kwargs...)
```

A LogoutButton component Logout button to submit a form post request to the `logout_url` prop. Usage is intended for dash-deployment-server authentication.

DDS usage:

`dcc.LogoutButton(logout_url=os.getenv('DASH_LOGOUT_URL'))`

Custom usage:

  * Implement a login mechanism.
  * Create a flask route with a post method handler.

`@app.server.route('/logout', methods=['POST'])`

  * The logout route should perform what's necessary for the user to logout.
  * If you store the session in a cookie, clear the cookie:

`rep = flask.Response(); rep.set_cookie('session', '', expires=0)`

  * Create a logout button component and assign it the logout_url

`dcc.LogoutButton(logout_url='/logout')`

See https://dash.plotly.com/dash-core-components/logout_button for more documentation and examples.

  * `id` (String; optional): Id of the button.
  * `className` (String; optional): CSS class for the button.
  * `label` (String; optional): Text of the button
  * `loading_state` (lists containing elements is*loading, prop*name, component*name   - `is*loading`(Bool; optional): Determines if the component is loading or not   -`prop*name`(String; optional): Holds which property is loading   -`component*name` (String; optional): Holds the name of the component that is loading; optional): Object that holds the loading state object coming from dash-renderer
  * `logout_url` (String; optional): Url to submit a post logout request.
  * `method` (String; optional): Http method to submit the logout form.
  * `style` (Dict; optional): Style of the button
