# next-remote-refresh

Utilize Fast Refresh for remote data in NextJS.

## Install

```bash
yarn add next-remote-refresh --dev
```

```bash
npm install next-remote-refresh --save-dev
```

## Usage

[View Example](/example)

Add plugin in `next.config.js`

```js
// next.config.js
const withRemoteRefresh = require('next-remote-refresh/plugin')({
  paths: [
    path.resolve(__dirname, './package.json'),
  ]
});

module.exports = withRemoteRefresh(nextConfig);
```

### `useRemoteRefresh`

```jsx
import { useRemoteRefresh } from 'next-remote-refresh'
import path from 'path'

function App({ name, version }) {
  useRemoteRefresh({
    shouldRefresh: (path) => {
      // do something based on changed file path
    },
  })
  return (
    <div>
      Package: {name} Version: {version}
    </div>
  )
}

export function useStaticProps() {
  return {
    props: path.resolve(process.cwd(), './package.json', 'utf-8'),
  }
}
```

## Development

```bash
yarn install && yarn build && yarn link
cd example
yarn install && yarn link next-remote-refresh
yarn dev
```

## Related

[next-remote-watch](https://github.com/hashicorp/next-remote-watch)
