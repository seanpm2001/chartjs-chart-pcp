# Chart.js Parallel Coordinate Plots

[![NPM Package][npm-image]][npm-url] [![Github Actions][github-actions-image]][github-actions-url]

Chart.js module for charting parallel coordinate plots (PCPs). Adding new chart type: `pcp`.

**Works only with Chart.js >= 2.9.0**

![MTCars](https://user-images.githubusercontent.com/4129778/79225882-bad80900-7e5d-11ea-89cf-f59f30987882.png)

[CodePen](https://codepen.io/sgratzl/pen/TODO)

![MTCars Tooltip](https://user-images.githubusercontent.com/4129778/79225877-b9a6dc00-7e5d-11ea-8dd4-ee554ebb6385.png)

![MTCars Tension](https://user-images.githubusercontent.com/4129778/79236173-e9a9ab80-7e6c-11ea-9f3c-28c4a3a79406.png)

## Install

```bash
npm install --save chart.js chartjs-chart-pcp
```

## Usage

see [Samples](https://github.com/sgratzl/chartjs-chart-pcp/tree/master/samples) on Github

## PCP

### Data Structure

the data items are the regular data items along with their labels. For each attribute there is an dataset. e.g., in the following example there are three items (A, B, C) with three axes / features (f1, f2, f3).

```js
const objs = [
  { label: 'A', f1: 5, f2: 3, f4: 3 },
  { label: 'B', f1: 2, f2: 1, f4: 8 },
  { label: 'C', f1: 10, f2: 6, f4: 2 },
];
const attrs = ['f1', 'f2', 'f3'];
const config = {
  data: {
    labels: objs.map((obj) => obj.label),
    datasets: attrs.map((attr) => ({
      label: attr,
      data: objs.map((obj) => obj[attr]),
    })),
  },
  options: {},
};
```

### Styling of elements

Two new elements were added: `lineSegment` as a subclass of line for a line segment between two axes and `linearAxis` for representing the vertical axis as a wrapper around a linear scale.

```ts
interface ILineSegmentOptions {
  // all options from
  // https://www.chartjs.org/docs/latest/charts/line.html#line-styling

  /**
   * line tension > 0 (e.g., 0.3) to create bezier curves
   * @default 0
   */
  tension: number;
}
```

```ts
interface ILinearAxisOptions {
  // all options from
  // https://www.chartjs.org/docs/latest/axes/cartesian/linear.html#linear-cartesian-axis
  /**
   * width of the visible axis
   * @default 30
   */
  axisWidth: number;
}
```

## Building

```sh
npm install
npm run build
```

[npm-image]: https://badge.fury.io/js/chartjs-chart-pcp.svg
[npm-url]: https://npmjs.org/package/chartjs-chart-pcp
[github-actions-image]: https://github.com/sgratzl/chartjs-chart-pcp/workflows/ci/badge.svg
[github-actions-url]: https://github.com/sgratzl/chartjs-chart-pcp/actions
