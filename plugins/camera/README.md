# Godot iOS Camera plugin

Uses Godot's `CameraServer` to handle iOS device camera feed.

## Methods

## Properties

## Events reporting

## Godot 4.5+ Features

### `get_formats()`

Returns an array of supported camera formats. Each entry is a Dictionary containing:

| Key | Type | Description |
|-----|------|-------------|
| `width` | int | Resolution width |
| `height` | int | Resolution height |
| `format` | String | Format name (BGRA_8888, 420f, 420v, etc.) |
| `frame_numerator` | int | Frame rate numerator |
| `frame_denominator` | int | Frame rate denominator |

### `set_format(index, parameters)`

Sets the camera format and parameters.

- `index`: Format index from `get_formats()`, or -1 to use default (1280x720)
- `parameters`: Dictionary with iOS-specific camera settings

#### iOS-specific Parameters

| Parameter | Values | Description |
|-----------|--------|-------------|
| `focus_mode` | `"locked"`, `"auto"`, `"continuous_auto"` | Focus mode |
| `exposure_mode` | `"locked"`, `"auto"`, `"continuous_auto"` | Exposure mode |
| `white_balance_mode` | `"locked"`, `"auto"`, `"continuous_auto"` | White balance mode |

Default is `continuous_auto` for all modes.

#### Example

```gdscript
var feed = CameraServer.get_feed(0)
var formats = feed.get_formats()

# Select a format and set parameters
feed.set_format(0, {
    "focus_mode": "continuous_auto",
    "exposure_mode": "auto"
})
```
