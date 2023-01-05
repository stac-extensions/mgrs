# MGRS Extension Specification

- **Title:** Military Grid Reference System
- **Identifier:** <https://stac-extensions.github.io/mgrs/v1.0.0/schema.json>
- **Field Name Prefix:** mgrs
- **Scope:** Item
- **Extension [Maturity Classification](https://github.com/radiantearth/stac-spec/tree/master/extensions/README.md#extension-maturity):** Pilot
- **Owner**: @matthewhanson

The MGRS STAC extension adds fields to Items to define their location within the [Military Grid Reference System](https://en.wikipedia.org/wiki/Military_Grid_Reference_System).

MGRS is commonly used system for distributing geospatial data. It divides the earth up by 
UTM zone (varies by longitude) and then by latitude band (varies by latitude). Within each 
of these regions the area is further subdivided into a 2D grid designated by 2 letters. 
In the polar regions a Universal Polar Stereographic (UPS) projection is used instead. 
The latitude band and grid squares are still used, but the UTM zone is not.

- Examples:
  - [Item example](examples/item.json): Shows the basic usage of the extension in a STAC Item
- [JSON Schema](json-schema/schema.json)
- [Changelog](./CHANGELOG.md)

## Item Properties

| Field Name           | Type                      | Description |
| -------------------- | --------| ----------- |
| mgrs:latitude_band   | string  | **REQUIRED**. The latitude band of the Item's centroid |
| mgrs:grid_square     | string  | **REQUIRED**. MGRS grid square of the Item's centroid |
| mgrs:utm_zone        | integer | The UTM Zone of the Item centroid |

Between 80°S and 84°N UTM Zone is required. In the polar regions UTM zone is not provided.

## Contributing

All contributions are subject to the
[STAC Specification Code of Conduct](https://github.com/radiantearth/stac-spec/blob/master/CODE_OF_CONDUCT.md).
For contributions, please follow the
[STAC specification contributing guide](https://github.com/radiantearth/stac-spec/blob/master/CONTRIBUTING.md) Instructions
for running tests are copied here for convenience.

### Running tests

The same checks that run as checks on PR's are part of the repository and can be run locally to verify that changes are valid. 
To run tests locally, you'll need `npm`, which is a standard part of any [node.js installation](https://nodejs.org/en/download/).

First you'll need to install everything with npm once. Just navigate to the root of this repository and on 
your command line run:
```bash
npm install
```

Then to check markdown formatting and test the examples against the JSON schema, you can run:
```bash
npm test
```

This will spit out the same texts that you see online, and you can then go and fix your markdown or examples.

If the tests reveal formatting problems with the examples, you can fix them with:
```bash
npm run format-examples
```
