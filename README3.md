### Cannot use JSX unless the '--jsx' flag is provided

I have looked around a bit for a solution to this problem. All of them suggest adding `"jsx": "react"` to your tsconfig.json file. Which I have done. Another one was to add `"include: []"`, which I have also done. However, I am still getting the error when I am trying to edit `.tsx`files. Below is my tsconfig file.

    {
        "compilerOptions": {
            "module": "commonjs",
            "target": "es5",
            "allowJs": true,
            "checkJs": false,
            "jsx": "react",
            "outDir": "./build",
            "rootDir": "./lib",
            "removeComments": true,
            "noEmit": true,
            "pretty": true,
            "skipLibCheck": true,
            "strict": true,
            "moduleResolution": "node",
            "esModuleInterop": true
        },
        "include": [
            "./lib/**/*"
        ],
        "exclude": [
            "node_modules"
        ]
    }

Any suggestions would be helpful. I am using babel 7 to compile all the code with the env, react and typescript presets. If you guys need more files to help debug this, let me know.

---

The problem is VSCode using an older version of typescript (4.0.3), while the typescript version shipped with the project is (4.1.2).
If you are seeing this issue after running create-react-app with Typescript You can solve this problem by adding `"typescript.tsdk": "node_modules/typescript/lib"` to `.vscode/settings.json`.

For IntelliSense, if you use `"jsx": "react-jsx"` you need to switch your workspace to use TS 4.1+

The following did the trick for me:

1. Go to the command palette <kbd>CTRL</kbd>+<kbd>Shift</kbd>+<kbd>P</kbd>.
2. Choose "TypeScript: Select a TypeScript Version...". (Probably 4.x.x something)
3. "Select TypeScript Version"
4. Select "Use Workspace Version version" which should reference `node_modules/typescript/lib`
