```
se_dict()
```

Getter function for the dictionary, representing the settings.yaml file.

Access to the dict is much slower than access to the setting struct, but more flexible.

Usage example: `z0 = se_dict()["environment"]["z0"]`
