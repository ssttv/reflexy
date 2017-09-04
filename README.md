# Reflexy [![npm package](https://img.shields.io/npm/v/reflexy.svg?style=flat-square)](https://www.npmjs.org/package/reflexy)

**Reflexy** is a React components for flexbox layout written in typescript.

With **Reflexy**
* You don't need to worry about the prefixes of different browsers - **Reflexy** use an [autoprefixer](https://github.com/postcss/autoprefixer).
* You don't need to do a concatenation of a lot of css classes:
  ```js
  <div className={classNames(styles['flex'], styles['flex-column'], styles['flex-align-center'], ...)}>{children}</div>
  ```
  vs
  ```js
  <Flex column alignItems="center" className="custom-class">{children}</Flex>
  ```
* You can replace default output `div` tag:
  ```js
  <Flex tagName="header">{children}</Flex>
  ```
  output:
  ```js
  <header class="...">{children}</header>
  ```
* You can tweak you own react component with flexbox layout (your component must accept className through props):
  ```js
  <Flex component={MyComponent} column alignSelf="center" myProp="myPropValue" className={styles['my-class']}>{children}</Flex>
  ```
  will be
  ```js
  <MyComponent myProp="myPropValue" className="[reflexy classes] my-class">{children}</MyComponent>
  ```

## Installation

```
yarn add react reflexy
```
or
```
npm install --save react reflexy
```

**Reflexy** has own css files so you need provide loader for css files placed in node_modules folder. With webpack it's maybe css-loader:
```js
{
  test: /\.css$/,
  include: path.join(__dirname, 'node_modules'),
  // or
  include: /reflexy/
  use: [
    { loader: 'style-loader' },
    {
      loader: 'css-loader',
      options: {
        modules: true,
        localIdentName: '[local]',
      },
    },
  ],
},
```

## Usage

```js
import { Flex } from 'reflexy';

...

<Flex row justifyContent="center">
  ...
</Flex>
```

## Props

### Flex

Default style is just `display: flex;`

* `inline?: boolean;` - Sets `display` to `inline-flex`.
* `alignContent?: 'center' | 'flex-start' | 'flex-end' | 'space-between' | 'space-around' | 'stretch';` - Sets `align-content` to corresponding value.
* `alignItems?: 'center' | 'flex-start' | 'flex-end' | 'stretch' | 'baseline';` - Sets `align-items` to corresponding value.
* `alignSelf?: 'center' | 'flex-start' | 'flex-end' | 'stretch' | 'baseline' | 'auto';` - Sets `align-self` to corresponding value.
* `justifyContent?: 'center' | 'flex-start' | 'flex-end' | 'space-between' | 'space-around';` - Sets `justify-content` to corresponding value.
* `basis?: 'none' | 'auto' | 'fill' | 'content' |fit-content' | 'min-content' | 'max-content';` - Sets `flex-basis` to corresponding value.
* `grow?: 0..24;` - Sets `flex-grow` to corresponding value.
* `shrink?: 0..24;` - Sets `flex-shrink` to corresponding value.
* `row?: boolean;` - Sets `flow-direction` to `row`.
* `column?: boolean;` - Sets `flow-direction` to `column`. Takes a precedence over `row`.
* `reverse?: boolean;` - Used with `row` or `col`. Sets `flow-direction` to `column-reverse` or `row-reverse`.
* `wrap?: boolean;` - Sets `flex-wrap` to `wrap`.
* `hfill?: boolean;` - Stretch by horizontal.
* `vfill?: boolean;` - Stretch by vertical.
* `fill?: 'v' | 'h' | 'all';` - Stretch by v - vertical or h - horizontal or all - both.
* `component?: React.ComponentType<any>;` - Sets React component as a container.
* `tagName?: string;` - Html tag name for output container. Takes a precedence over `component`.
* and all other props of html element.

## TODO

- [x] `flex-grow`
- [x] `flex-shrink`

## License

[MIT](https://opensource.org/licenses/mit-license.php)
