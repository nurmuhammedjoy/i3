# Rounded Frame Corners in i3

This fork of i3 supports rounded corners on window frames via the `border_radius` configuration directive.

## Requirements

Rounded corners rely on the X11 **SHAPE** extension. Most modern X servers include it by default. i3 will silently ignore the `border_radius` setting if the extension is unavailable.

## Configuration

Add the following line to your i3 config file (typically `~/.config/i3/config` or `~/.i3/config`):

```
border_radius <radius>[px]
```

`<radius>` is the corner radius in pixels. A value of `0` (the default) disables rounded corners.

### Examples

```
# 8 px rounded corners
border_radius 8

# Equivalent — the "px" suffix is optional
border_radius 8px

# Disable rounded corners (default)
border_radius 0
```

## Notes

- The radius is automatically clamped to `MIN(window_width, window_height) / 2` so the shape always fits inside the frame.
- Rounded corners are applied to all **leaf** containers (individual windows), whether tiled or floating.
- When combined with gaps (see [Gaps](userguide#gaps) in the user guide), the rounded outline and the gap spacing complement each other visually.
- If a client window has its own custom shape (e.g. a shaped overlay), i3 intersects it with the rounded shape so both the rounded outline and the client shape are respected.

## Reloading the configuration

After editing your config file, reload i3 to apply the change:

```
$mod+Shift+r
```

Or via `i3-msg`:

```sh
i3-msg reload
```
