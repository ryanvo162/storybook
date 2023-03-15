# Build Professional User Interfaces with Storybook

Storybook is a tool that allows you to develop complex user interface (UI) and interactions of your application in an isolated environment. With Storybook, you can build individual components and develop them independently from your application.

## Key features of Storybook

* **Independent development:** Storybook allows you to develop individual components without needing to build or run your application.
* **Annotation and documentation of components:** Storybook allows you to document your components using Markdown annotations.
* **Interaction and testing:** Storybook allows you to interact with your components and test them in various scenarios, including different states of the component.
* **Easy sharing:** Storybook allows you to easily share your components with colleagues and clients.

## Related technologies

* **React:** Storybook is designed for React, a popular JavaScript library for developing user interfaces. React components can be easily developed and tested in Storybook, making it a popular choice for React developers.
* **TypeScript:** Storybook supports TypeScript, a popular programming language for developing JavaScript applications. TypeScript provides static type checking and other features that can help improve the quality of your code.
* **Jest:** Jest is a popular JavaScript testing framework, often used to test UI components developed with Storybook. Jest provides a simple and intuitive API for writing tests, and can be easily integrated with Storybook. [Learn more about Jest](https://jestjs.io/).
* **CSS-in-JS libraries:** Many CSS-in-JS libraries, such as Styled Components and Emotion, are designed to work well with Storybook. This allows you to develop and test your UI components with the same styling solution you use in your application.
* **Design systems:** Storybook is often used in conjunction with design systems, which provide a set of reusable UI components and design guidelines for building applications. Storybook can be used to develop, test, and document components in a design system, ensuring consistency across your application.

Overall, Storybook can be used with a wide range of technologies to develop and test high-quality UI components for your application.

## Getting started

To get started with Storybook, you can follow the official [Storybook tutorial](https://storybook.js.org/tutorials/intro-to-storybook/react/en/get-started/).

### Prerequisites

To follow the tutorial, you will need the following:

* [Node.js](https://nodejs.org/en/) installed on your machine.
* A basic understanding of React and JavaScript.

### Tutorial

The tutorial will walk you through the process of setting up Storybook and creating a simple component. You can follow the tutorial.

#### Step 1: Create a React application, using TypeScript

The first step is to create a React application using [Create React App](https://create-react-app.dev/). Create React App is a popular tool for creating React applications, and provides a simple way to get started with React.

To create a React application, run the following command:

```bash
npx create-react-app test_sb --template typescript
```

This will create a new React application in a directory called `test_sb`. You can then navigate to the directory and start the application:

```bash
cd test_sb
yarn start
```

<!-- add storybook and create a button primary, second, triary, small, normal, big -->

#### Step 2: Add Storybook, configure it

To add Storybook to your application, run the following command:

```bash
npx sb init
```

This will add Storybook to your application. You can then start Storybook by running the following command:

```bash
yarn storybook
```

#### Step 3: Create a component

The next step is to create a simple component. In this tutorial, you will create a simple button component.

To create a button component, create a new file called `Button.tsx` in the `src/components` directory. Add the following code to the file:

```tsx
import React from 'react';

interface ButtonProps {
  /**
   * Is this the principal call to action on the page?
   */
  primary?: boolean;
  /**
   * What background color to use
   */
  backgroundColor?: string;
  /**
   * How large should the button be?
   */
  size?: 'small' | 'medium' | 'large';
  /**
   * Button contents
   */
  label: string;
  /**
   * Optional click handler
   */
  onClick?: () => void;
}

/**
 * Primary UI component for user interaction
 */
export const Button: React.FC<ButtonProps> = ({
  primary = false,
  size = 'medium',
  backgroundColor,
  label,
  ...props
}) => {
  const mode = primary
    ? 'storybook-button--primary'
    : 'storybook-button--secondary';
  return (
    <button
      type="button"
      className={['storybook-button', `storybook-button--${size}`, mode].join(
        ' '
      )}
      style={backgroundColor && { backgroundColor }}
      {...props}
    >
      {label}
    </button>
  );
};
```

This will create a simple button component. You can then import the component into the `App.tsx` file and use it in the application:

```tsx
import React from 'react';
import { Button } from './components/Button';

function App() {
  return (
    <div className="App">
      <Button label="Hello Button" />
    </div>
  );
}

export default App;
```

#### Step 4: Create a story

The next step is to create a story for the button component. A story is a piece of code that defines how a component should be rendered in Storybook.

To create a story for the button component, create a new file called `Button.stories.tsx` in the `src/components` directory. Add the following code to the file:

```tsx
import React from 'react';
import { ComponentStory, ComponentMeta } from '@storybook/react';

import { Button } from './Button';

export default {
  title: 'Example/Button',
  component: Button,
  argTypes: {
    backgroundColor: { control: 'color' },
  },
} as ComponentMeta<typeof Button>;

const Template: ComponentStory<typeof Button> = (args) => <Button {...args} />;
```

This will create a story for the button component. You can then add stories for the different states of the button component:

```tsx
export const Primary = Template.bind({});
Primary.args = {
  primary: true,
  label: 'Button',
};

export const Secondary = Template.bind({});
Secondary.args = {
  label: 'Button',
};

export const Large = Template.bind({});
Large.args = {
  size: 'large',
  label: 'Button',
};

export const Small = Template.bind({});
Small.args = {
  size: 'small',
  label: 'Button',
};
```

#### Step 5: Configure Storybook

The next step is to configure Storybook. Storybook can be configured using the `main.js` file in the `.storybook` directory.

To configure Storybook, open the `main.js` file and add the following code:

```js
module.exports = {
  stories: ['../src/components/**/*.stories.tsx'],
  addons: ['@storybook/addon-links', '@storybook/addon-essentials'],
};
```

This will configure Storybook to load stories from the `src/components` directory.

#### Step 6: Build Storybook

The final step is to build Storybook. To build Storybook, run the following command:

```bash
yarn build-storybook
```

This will build Storybook and output it to the `storybook-static` directory.

## Conclusion

In this tutorial, you learned how to use Storybook to develop and test UI components for your application. You also learned how to configure Storybook and build it.

## Resources

* [Storybook](https://storybook.js.org/)
* [Storybook tutorial](https://storybook.js.org/tutorials/intro-to-storybook/react/en/get-started/)
* [Create React App](https://create-react-app.dev/)
* [React](https://reactjs.org/)
* [TypeScript](https://www.typescriptlang.org/)
* [Node.js](https://nodejs.org/en/)
* [Yarn](https://yarnpkg.com/)
* [npm](https://www.npmjs.com/)
